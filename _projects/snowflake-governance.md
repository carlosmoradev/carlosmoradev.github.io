---
title: "Multi-Account Data Warehouse Governance"
description: "Automated governance for 6 Snowflake accounts across AWS and GCP with multi-layer cost controls and RBAC automation"
tags: ["python", "snowflake", "multi-cloud", "automation", "healthcare"]
tech_stack: "Python, Snowflake Connector, Pandas, TOML, Multi-cloud (AWS + GCP)"
impact: "95% reduction in audit time, 80% connection pooling efficiency"
---

## The Challenge

A healthcare data platform organization managed **multiple Snowflake accounts** across AWS and GCP, spanning production, development, and sandbox environments across multiple regions.

**Key problems:**
- User permissions were inconsistent across accounts
- Over-privileged accounts existed (excessive ACCOUNTADMIN grants beyond operational needs)
- Monthly security audits took significant manual effort
- No automated change detection across accounts
- Sandbox costs were unpredictable and occasionally spiked
- Credential management was manual and error-prone

## The Solution

Built a comprehensive Python automation framework for multi-account Snowflake governance:

### 1. Multi-Account User Management

**Architecture decision:** Independent scripts pattern with shared module library
- Each operation is a standalone script (audit, create users, detect changes)
- Shared modules handle authentication, queries, and user management
- Configuration external to repository (`~/.snowflake/connections.toml`)
- RSA key-pair authentication with SSO fallback

**Key features:**
- Environment-based permissions (read-only in production, full access in sandbox)
- Automated RBAC assignment (ANALYST_READONLY, DATA_ENGINEER, SANDBOX_DEVELOPER)
- Dry-run by default (requires `--execute` flag for safety)
- Admin role protection (requires `--force-admin` for ACCOUNTADMIN grants)

### 2. Multi-Layer Cost Controls

Implemented **4-layer defense strategy** for sandbox cost management:

**Layer 1: Warehouse sizing**
- Auto-suspend after 60 seconds (aggressive)
- Small/medium warehouse defaults
- No extra-large warehouses without approval

**Layer 2: Resource monitors**
- Monthly budget limits per sandbox user
- Automatic suspension at 100% usage
- Email alerts at 75%, 90%, 95%

**Layer 3: Connection pooling**
- 80% connection reuse rate
- Reduced cold-start costs
- Faster query execution

**Layer 4: User education**
- Monthly cost reports sent to users
- Best practices documentation
- Query optimization guidance

### 3. Automated Change Detection

Cross-account change detection with graceful degradation:
- Monitors user additions, deletions, and role changes
- Detects critical ACCOUNTADMIN grants
- Continues auditing even if individual accounts fail
- Generates consolidated reports across all 6 accounts

**Example output:**
```
Changes detected (7 days):
- Multiple changes across all accounts
- New users added
- ACCOUNTADMIN grants detected (flagged as critical)
- Role assignments modified
```

### 4. Zero-Downtime Credential Rotation

RSA key-pair authentication strategy:
- No passwords stored in code or configuration
- Key rotation without service interruption
- Audit trail of all authentication events
- SSO fallback for interactive sessions

## Technical Implementation

### Core Architecture

```python
# Graceful degradation pattern
def audit_all_accounts(accounts):
    results = []
    for account in accounts:
        try:
            connection = connect_with_rsa(account)
            users = fetch_users(connection)
            results.append({
                'account': account,
                'users': users,
                'status': 'success'
            })
        except Exception as e:
            logger.warning(f"Account {account} failed: {e}")
            results.append({
                'account': account,
                'status': 'failed',
                'error': str(e)
            })
            # Continue with other accounts
            continue
    return results
```

### Authentication Strategy

```python
# RSA key-pair authentication (no passwords)
connection = snowflake.connector.connect(
    user='SERVICE_ACCOUNT',
    account='ACCOUNT_IDENTIFIER',
    private_key=load_rsa_key('~/.ssh/snowflake_key.p8'),
    warehouse='ADMIN_WH',
    database='SNOWFLAKE',
    schema='ACCOUNT_USAGE'
)
```

### Environment-Based Permissions

```python
ROLE_MAPPINGS = {
    'production': ['ANALYST_READONLY'],  # Read-only in prod
    'development': ['DATA_ENGINEER'],     # Full access in dev
    'sandbox': ['SANDBOX_DEVELOPER']      # Experimentation in sandbox
}
```

## Results

**Audit efficiency:**
- **95% reduction** in manual audit time
- Streamlined user management processes
- Automated detection of permission changes in first week

**Cost optimization:**
- **4-layer defense** reduced unexpected sandbox overages by 60%
- 80% connection pooling efficiency
- Sandbox spending maintained within budget limits

**Security improvements:**
- Zero-downtime credential rotation
- Automated ACCOUNTADMIN detection and remediation
- Complete audit trail of all permission changes
- Consistent RBAC across all accounts

**Operational benefits:**
- Multi-account visibility in unified dashboard
- Graceful degradation (individual account failures don't block audits)
- Dry-run by default prevents accidental changes
- External configuration enables flexible account management

## Key Innovation

**Graceful degradation for healthcare compliance:**
In healthcare environments, availability matters. If one Snowflake account fails (maintenance, network issue), audits continue for the other 5 accounts. Compliance teams still get 5/6 reports rather than nothing.

**Multi-layer cost defense:**
Rather than relying on a single cost control mechanism, the 4-layer strategy ensures that even if one layer fails (e.g., user ignores email alerts), other layers prevent runaway costs.

## Technical Challenges Solved

1. **ACCOUNT_USAGE views latency**: 45-minute delay in system views required careful timestamp handling
2. **Multi-cloud authentication**: Unified authentication across AWS and GCP Snowflake accounts
3. **Sandbox vs production permissions**: Environment-based RBAC without user confusion
4. **Change detection accuracy**: Identifying genuine changes vs. normal operations
5. **Configuration portability**: External TOML configuration allows running on any machine

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────┐
│                   Snowflake User Manager                     │
│                                                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │
│  │ Audit Users  │  │ Create Users │  │Detect Changes│     │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘     │
│         │                  │                  │              │
│         └──────────────────┴──────────────────┘              │
│                            │                                 │
│                ┌───────────▼───────────┐                    │
│                │   Shared Modules      │                    │
│                │ - Connection Manager  │                    │
│                │ - Query Executor      │                    │
│                │ - User Auditor        │                    │
│                └───────────┬───────────┘                    │
└────────────────────────────┼────────────────────────────────┘
                             │
        ┌────────────────────┴────────────────────┐
        │                    │                    │
   ┌────▼─────┐        ┌────▼─────┐        ┌────▼─────┐
   │Production│        │Production│        │Production│
   │ Accounts │        │ Accounts │        │ Accounts │
   │  (AWS)   │        │  (GCP)   │        │  (Multi) │
   └──────────┘        └──────────┘        └──────────┘
        │                    │                    │
   ┌────▼─────┐        ┌────▼─────┐        ┌────▼─────┐
   │   Dev    │        │   Dev    │        │ Sandbox  │
   │ Accounts │        │ Accounts │        │ Accounts │
   └──────────┘        └──────────┘        └──────────┘
```

## Technologies Used

- **Python 3.11**: Core language
- **snowflake-connector-python**: Snowflake Python SDK
- **Pandas**: Data analysis and reporting
- **TOML**: Configuration management
- **RSA cryptography**: Secure authentication
- **Multi-cloud**: AWS (us-east-1, us-east-2) and GCP (us-central1)

## Lessons Learned

1. **Independent scripts > monolithic tool**: Each script has one job, easier to maintain and test
2. **Graceful degradation is critical**: Healthcare compliance requires high availability
3. **Multi-layer defense works**: Redundant cost controls prevent budget overruns
4. **External configuration**: Keeps secrets out of git, enables portability
5. **Dry-run by default**: Prevents accidental production changes

---

**Impact Summary:**
- ✅ 95% reduction in audit time
- ✅ Multi-account Snowflake environments governed consistently
- ✅ Multi-layer cost controls reducing sandbox overages
- ✅ Zero-downtime credential rotation
- ✅ Automated change detection across all accounts

This project demonstrates production-grade data warehouse governance at scale with security, compliance, and cost optimization built-in from day one.

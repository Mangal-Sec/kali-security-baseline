# Account Management Policy

## 1. Purpose

This policy defines the requirements for managing local user accounts on the Kali Linux system.

The objective is to ensure that user accounts are created, used, maintained, and disabled according to documented security requirements and the principle of least privilege.

## 2. Scope

This policy applies to all local user accounts on the system, including:

* Administrative accounts
* Development accounts
* Security testing and research accounts
* Default or legacy accounts

## 3. Account Roles

The system will maintain separate accounts for distinct operational responsibilities.

### 3.1 Administrative Account

The administrative account is responsible for system-level administration and security configuration.

Administrative privileges must be used only when required for authorized system administration tasks.

The administrative account should not be used for routine development, browsing, or security testing activities.

### 3.2 Development Account

The development account is intended for software development and related activities.

The account should operate with standard user privileges unless a specific documented requirement requires additional authorization.

Development activities should be performed within user-owned resources whenever possible.

### 3.3 Security Account

The security account is intended for authorized security research, vulnerability assessment, penetration testing, and security laboratory activities.

The account should operate with the minimum privileges required for the specific security tools and activities being performed.

Security testing involving intentionally vulnerable or untrusted systems should use additional isolation where appropriate.

## 4. Account Creation

New local accounts must have:

* A unique username.
* A defined operational purpose.
* A defined owner or responsible role.
* Only the group memberships required for their intended activities.
* No unnecessary administrative privileges.

Account creation should be documented when the account is part of the security baseline.

## 5. Privilege Assignment

Privileges must be assigned according to the principle of least privilege.

Users must not receive administrative privileges merely for convenience.

Additional privileges must have:

1. A defined purpose.
2. A documented requirement.
3. An appropriate authorization mechanism.
4. A verification procedure.

## 6. Account Authentication

Local accounts must use individual authentication credentials.

Credentials must not be shared between users or roles.

Authentication configuration must follow the system's applicable security requirements.

## 7. Login Access

Interactive login access must be limited to accounts that require it.

Accounts that are not intended for interactive use should not provide unnecessary interactive login capability.

Disabled or decommissioned accounts must not remain usable for authentication.

## 8. Default and Legacy Accounts

Default or legacy accounts must be reviewed before being disabled or removed.

Before changing such an account, the following must be verified:

* Whether the account is currently used.
* Whether system services depend on it.
* Whether files are owned by the account.
* Whether scheduled tasks depend on it.
* Whether an alternative administrative account is available.
* Whether recovery access has been tested.

Disabling an account is preferred over deleting it when preservation of its files or account information is required.

## 9. Account Review

User accounts and their privileges should be periodically reviewed.

The review should identify:

* Unused accounts.
* Unexpected accounts.
* Unnecessary group memberships.
* Unnecessary administrative privileges.
* Accounts that should be disabled.

## 10. Account Decommissioning

When an account is no longer required, its access must be revoked.

The decommissioning process should consider:

1. Disabling authentication.
2. Reviewing owned files.
3. Reviewing scheduled tasks and services.
4. Reviewing group memberships.
5. Preserving required evidence or data.
6. Removing the account only when appropriate.

## 11. Security Principle

Account management must support:

* Least Privilege
* Separation of Duties
* Accountability
* Controlled Access
* Secure Decommissioning

Account configuration must be based on documented requirements rather than convenience.

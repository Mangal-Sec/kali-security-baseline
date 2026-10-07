# Sudo Policy

## 1. Purpose

This policy defines requirements for the use and management of `sudo` on the Kali Linux system.

The objective is to control privileged operations and ensure that administrative access is granted only when required and authorized.

## 2. Scope

This policy applies to:

* Local user accounts
* Sudo-enabled accounts
* Sudoers configuration
* Privileged commands
* Administrative operations
* Security tools requiring elevated privileges

## 3. Sudo Principles

Sudo access must follow:

* Least Privilege
* Explicit Authorization
* Separation of Duties
* Accountability
* Controlled Privilege Escalation

Users must not receive unrestricted sudo access solely for convenience.

## 4. Administrative Access

Administrative privileges should be assigned to a designated administrative role.

Administrative access must be used only for authorized system administration tasks.

Routine development and security-testing activities should not be performed through unrestricted root access.

## 5. Command Authorization

Where elevated privileges are required for a specific operational task, access should be limited to the minimum command or command set required.

Broad command authorization should be avoided when a narrower authorization is technically practical.

## 6. Development Role

The development role should not receive unrestricted administrative privileges by default.

Development tasks should normally be performed using standard user privileges and isolated development environments.

When a development requirement needs administrative access, the requirement must be explicitly identified and evaluated before authorization is granted.

## 7. Security Role

The security role should not receive unrestricted administrative privileges by default.

Security tools that require elevated privileges should be evaluated individually.

Where technically feasible, the required capability or narrowly scoped privilege should be used instead of unrestricted root access.

Security testing must remain within authorized environments.

## 8. Sudo Configuration

Sudo configuration must be managed through controlled configuration files and should not be modified casually.

Changes to sudo authorization must be documented.

The configuration must be reviewed after changes to ensure that unintended privileges have not been introduced.

## 9. Password Authentication

Sudo authentication requirements must follow the system's security requirements.

Passwordless privilege escalation should not be enabled unless there is a documented operational requirement and an appropriate risk assessment.

## 10. Privilege Escalation

Users must not use privileged access to bypass established access-control policies.

Privilege escalation must have a legitimate administrative or operational purpose.

Unexpected privilege escalation paths must be investigated.

## 11. Logging and Accountability

Privileged operations performed through `sudo` should remain attributable to the individual user account that initiated the operation.

Sudo-related logs should be retained according to the system's logging requirements.

Logs may be used during security verification and incident investigation.

## 12. Sudoers Review

Sudo authorization must be periodically reviewed for:

* Unnecessary sudo access
* Overly broad command permissions
* Passwordless privileges
* Unexpected users
* Deprecated authorization rules
* Privileges no longer required

## 13. Emergency Administrative Access

Emergency administrative access must remain available through an authorized administrative mechanism.

Emergency access must not be implemented by granting unrestricted privileges to every operational user.

Emergency actions should be documented when practical.

## 14. Verification

Sudo configuration must be tested after implementation.

Verification should confirm:

1. Authorized administrative operations succeed.
2. Unauthorized privileged operations are denied.
3. Development users do not receive unintended administrative privileges.
4. Security users do not receive unintended administrative privileges.
5. Sudo activity is appropriately logged.

Verification results must be documented in:

`04-verification/security-test-cases.md`

## 15. Security Principle

Administrative privileges are an exception to normal user access and must therefore be explicitly authorized, narrowly scoped where practical, and auditable.

The objective is to make privileged access controlled and traceable rather than convenient and unrestricted.

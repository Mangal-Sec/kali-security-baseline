# Kali Linux Security Architecture

## 1. Purpose

This document defines the security architecture for the Kali Linux system used for development, security research, and authorized security testing.

The architecture is designed around established security principles including:

* Least Privilege
* Privilege Separation
* Separation of Duties
* Defense in Depth
* Access Control
* Accountability
* Secure Configuration
* Security Lab Isolation

The objective is to reduce unnecessary privilege, limit the impact of a compromised user account, separate different types of activity, and provide a documented and verifiable security baseline.

## 2. Scope

This security architecture covers:

* Local user accounts
* User and group privileges
* Administrative access
* Filesystem access control
* Security tool access
* Authentication and authorization
* Security logging and auditing
* Host-level security controls
* Security lab isolation
* Security configuration verification

This document defines the intended security architecture. Detailed configuration requirements and implementation procedures are documented separately.

## 3. Security Objectives

The architecture has the following objectives:

1. Provide separate identities for different operational roles.
2. Apply the principle of least privilege.
3. Minimize unnecessary administrative privileges.
4. Separate development, security testing, and system administration activities.
5. Restrict access to protected resources according to defined authorization requirements.
6. Maintain sufficient logging and accountability for security-relevant activities.
7. Isolate security testing environments from the primary operating environment where appropriate.
8. Make security controls measurable and verifiable.

## 4. Architectural Principle

Security controls will be implemented in layers rather than relying on a single control.

```text
Identity
   ↓
Authentication
   ↓
Authorization
   ↓
Least Privilege
   ↓
Isolation
   ↓
Logging & Auditing
   ↓
Verification
   ↓
Recovery
```

Each layer provides a different security function. Failure of one control should not automatically result in unrestricted system access.

## 5. Design Approach

The system will be designed using a role-based model.

Operational activities will be separated according to their security requirements rather than providing every activity with the same level of privilege.

The initial roles are:

* Administrative role
* Development role
* Security testing and research role

The exact permissions associated with each role will be defined in the project's access-control and account policies.

## 6. Security Boundary

A local Linux user account is considered an authorization boundary for user-owned resources, but it is not treated as a complete security isolation boundary.

Stronger isolation will be used where required, particularly for security testing involving intentionally vulnerable systems or untrusted software.

Virtual machines, containers, and isolated networks may be used as additional security boundaries depending on the laboratory requirements.

## 7. Configuration Philosophy

The system will follow these principles:

* Access will be granted based on documented requirements.
* Administrative privileges will not be granted by default.
* Security-sensitive operations will require explicit authorization.
* Security controls will be verified after implementation.
* Configuration changes will be documented.
* Security-relevant assumptions will be explicitly identified rather than silently introduced.

## 8. Related Documents

The following documents define specific controls and implementation details:

* `02-policies/account-policy.md`
* `02-policies/access-control-policy.md`
* `02-policies/sudo-policy.md`
* `03-implementation/implementation-log.md`
* `04-verification/security-test-cases.md`
* `05-audit/audit-report.md`

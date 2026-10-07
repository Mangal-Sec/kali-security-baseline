# Access Control Policy

## 1. Purpose

This policy defines how access to system resources is authorized and restricted on the Kali Linux system.

The objective is to ensure that users and processes receive only the access required for their authorized activities.

## 2. Scope

This policy applies to:

* Files and directories
* User-owned resources
* Shared resources
* System resources
* Security tools
* Development resources
* Administrative resources
* Security laboratory resources

## 3. Access Control Principles

Access control will follow these principles:

* Least Privilege
* Default Deny where appropriate
* Explicit Authorization
* Separation of Duties
* Need-to-Know
* Complete Mediation
* Accountability

Access must be granted based on a documented requirement rather than convenience.

## 4. User Access

Each user must have an individual account.

Users must not share accounts or authentication credentials.

Access to resources must be based on the user's assigned role and required activities.

## 5. File and Directory Access

Filesystem permissions must be configured according to ownership and operational requirements.

Protected resources must not be made broadly accessible when a narrower permission scope is sufficient.

User-owned resources should normally remain accessible only to the owning user unless sharing is explicitly required.

Sensitive system resources must remain protected from unauthorized modification.

## 6. Group-Based Access

Linux groups may be used to provide access to resources shared by multiple authorized users.

Group membership must have a defined purpose.

Users must not be added to privileged groups solely for convenience.

Group membership should be reviewed periodically.

## 7. Administrative Access

Administrative access must be restricted to authorized administrative operations.

Standard development and security-testing activities should not require unrestricted administrative privileges.

Where elevated access is required, the access mechanism should provide the minimum privilege necessary for the task.

## 8. Security Tool Access

Security tools must be available to the security role when required for authorized security research and testing.

Where a tool requires elevated privileges, the minimum required privilege should be provided rather than granting unrestricted administrative access.

Security tools must only be used against systems and resources for which authorization exists.

## 9. Development Resources

Development resources should be separated from protected system resources.

Development activities should use user-owned project directories and isolated environments where practical.

System-wide modifications must require appropriate authorization.

## 10. Security Laboratory Resources

Security laboratory resources should be isolated from the primary operating environment where the risk of compromise warrants additional containment.

Intentionally vulnerable systems, untrusted software, and exploit-development environments should preferably be operated within dedicated virtual machines, containers, or isolated networks.

Access to laboratory resources must be limited to the users and processes that require it.

## 11. Privileged Groups

Membership in privileged groups must be explicitly justified.

Examples of potentially sensitive groups include groups that provide access to:

* Administrative functions
* Network interfaces
* Packet capture
* Containers
* Virtualization
* Hardware devices
* System management functions

Group membership must be reviewed before granting access.

## 12. Access Review

Access permissions must be periodically reviewed.

Reviews should identify:

* Excessive permissions
* Unnecessary group memberships
* Unexpected access
* Orphaned resources
* Resources with overly broad permissions

## 13. Access Revocation

Access must be revoked when:

* The user no longer requires the resource.
* The user's role changes.
* A privilege is no longer justified.
* An account is disabled or decommissioned.
* A security requirement changes.

## 14. Verification

Access-control configurations must be tested after implementation.

Verification should confirm both:

1. Authorized users can perform required operations.
2. Unauthorized users are denied access.

Test results must be documented in:

`04-verification/security-test-cases.md`

## 15. Security Principle

Access decisions must be explicit, documented, and enforceable.

The goal is not to eliminate all access, but to ensure that every granted privilege has a legitimate operational purpose.

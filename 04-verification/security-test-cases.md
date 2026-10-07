# Security Test Cases

## 1. Purpose

This document defines verification tests for the Kali Linux security baseline.

The objective is to verify that implemented security controls enforce the documented security architecture and policies.

Testing must confirm both:

* Authorized actions succeed as intended.
* Unauthorized actions are denied as intended.

---

## 2. Testing Principles

All verification activities should follow these principles:

* Test the actual system state.
* Verify controls against documented requirements.
* Test both positive and negative access cases.
* Avoid making configuration changes during verification unless explicitly authorized.
* Record observed results.
* Investigate unexpected privilege or access.
* Do not treat configuration presence alone as proof of effective control.

---

## 3. Account Management Tests

### TC-001 — Verify Required Accounts

**Objective:**
Confirm that required administrative, development, and security identities exist as documented.

**Expected Result:**
Required accounts exist and have the intended role.

**Status:** Not Tested

---

### TC-002 — Verify Unnecessary Accounts

**Objective:**
Identify unused, unexpected, or legacy local accounts.

**Expected Result:**
No unexplained accounts exist. Legacy accounts are documented, disabled, or removed according to policy.

**Status:** Not Tested

---

### TC-003 — Verify Account Separation

**Objective:**
Confirm that administrative, development, and security activities use appropriately separated identities.

**Expected Result:**
Routine development and security activities do not require unrestricted administrative accounts.

**Status:** Not Tested

---

## 4. Group and Privilege Tests

### TC-004 — Verify Group Membership

**Objective:**
Review privileged and security-sensitive group memberships.

**Expected Result:**
Users belong only to groups required for their documented role.

**Status:** Not Tested

---

### TC-005 — Verify Administrative Privileges

**Objective:**
Determine which accounts have administrative privileges.

**Expected Result:**
Administrative privileges are limited to authorized accounts and justified requirements.

**Status:** Not Tested

---

### TC-006 — Verify Least Privilege

**Objective:**
Determine whether a standard user can perform privileged operations without explicit authorization.

**Expected Result:**
Privileged operations are denied unless an authorized privilege-escalation mechanism is used.

**Status:** Not Tested

---

## 5. Sudo Tests

### TC-007 — Verify Sudo Authorization

**Objective:**
Determine which users and commands are authorized through `sudo`.

**Expected Result:**
Sudo access matches the documented sudo policy.

**Status:** Not Tested

---

### TC-008 — Verify Unauthorized Sudo Access

**Objective:**
Confirm that users without administrative authorization cannot obtain unrestricted administrative access through `sudo`.

**Expected Result:**
Unauthorized users are denied unrestricted administrative access.

**Status:** Not Tested

---

### TC-009 — Verify Sudo Logging

**Objective:**
Confirm that privileged operations performed through `sudo` are attributable to the initiating user.

**Expected Result:**
Sudo activity is recorded through the system's applicable logging mechanism.

**Status:** Not Tested

---

## 6. Filesystem Access Tests

### TC-010 — Verify Protected Resource Access

**Objective:**
Attempt access to protected system resources using a non-privileged account.

**Expected Result:**
Unauthorized access is denied.

**Status:** Not Tested

---

### TC-011 — Verify User-Owned Resource Access

**Objective:**
Confirm that users can access and modify resources they are authorized to manage.

**Expected Result:**
Authorized access succeeds without requiring unnecessary administrative privileges.

**Status:** Not Tested

---

### TC-012 — Verify Cross-User Access

**Objective:**
Test whether one standard user can improperly modify another user's protected resources.

**Expected Result:**
Unauthorized modification is denied.

**Status:** Not Tested

---

## 7. Privileged Binary Tests

### TC-013 — Identify SUID/SGID Objects

**Objective:**
Identify SUID and SGID files and determine whether each has a documented purpose.

**Expected Result:**
Privileged binaries are known, justified, and reviewed.

**Status:** Not Tested

---

### TC-014 — Review Unexpected Privilege Paths

**Objective:**
Identify binaries or configurations that may provide unintended privilege escalation paths.

**Expected Result:**
No unexplained or unnecessary privileged execution paths exist.

**Status:** Not Tested

---

## 8. Security Tool Access Tests

### TC-015 — Verify Security Tool Authorization

**Objective:**
Confirm that security-sensitive tools are available only to authorized users and are used only against authorized targets.

**Expected Result:**
Tool access and elevated capabilities match documented requirements.

**Status:** Not Tested

---

### TC-016 — Verify Security Tool Privilege Boundaries

**Objective:**
Determine whether security tools require more privilege than necessary.

**Expected Result:**
Tools operate with the minimum privileges required for their intended function.

**Status:** Not Tested

---

## 9. Development Environment Tests

### TC-017 — Verify Development Isolation

**Objective:**
Confirm that development projects and virtual environments are stored in appropriate user-controlled locations.

**Expected Result:**
Development activity does not require unnecessary modification of protected system resources.

**Status:** Not Tested

---

### TC-018 — Verify Development Privilege Restrictions

**Objective:**
Determine whether routine development activities can be performed without unrestricted administrative privileges.

**Expected Result:**
Normal development workflows operate under standard-user privileges.

**Status:** Not Tested

---

## 10. Lab Isolation Tests

### TC-019 — Verify Lab Separation

**Objective:**
Confirm that security testing environments are appropriately isolated from protected host resources.

**Expected Result:**
Lab resources are separated using appropriate mechanisms such as containers, virtual machines, or isolated networks.

**Status:** Not Tested

---

### TC-020 — Verify Lab-to-Host Boundaries

**Objective:**
Determine whether a compromised or intentionally vulnerable lab system can access protected host resources beyond the documented boundary.

**Expected Result:**
Access is restricted to the explicitly authorized lab boundary.

**Status:** Not Tested

---

## 11. Logging and Auditing Tests

### TC-021 — Verify Security-Relevant Logging

**Objective:**
Confirm that relevant authentication, authorization, and privileged activity is logged where required.

**Expected Result:**
Security-relevant events are recorded through the configured logging mechanisms.

**Status:** Not Tested

---

### TC-022 — Verify Log Accountability

**Objective:**
Confirm that security-relevant actions can be associated with the responsible account or process where technically applicable.

**Expected Result:**
Logs provide sufficient information for security investigation and accountability.

**Status:** Not Tested

---

## 12. Configuration Verification

### TC-023 — Verify Implemented Baseline

**Objective:**
Compare the actual system configuration against the documented intended state.

**Expected Result:**
Implemented controls match the approved security baseline.

**Status:** Not Tested

---

### TC-024 — Identify Configuration Drift

**Objective:**
Identify security-relevant configuration changes that are not documented in the implementation log.

**Expected Result:**
No unexplained security-relevant configuration drift exists.

**Status:** Not Tested

---

## 13. Recovery and Administrative Access

### TC-025 — Verify Administrative Recovery Path

**Objective:**
Confirm that an authorized recovery path exists if the primary administrative account becomes unavailable.

**Expected Result:**
A documented and controlled recovery mechanism exists.

**Status:** Not Tested

---

## 14. Test Result Classification

Each test should be classified as:

* **PASS** — Control behaves as intended.
* **FAIL** — Control does not satisfy the documented requirement.
* **PARTIAL** — Control is implemented but does not fully satisfy the requirement.
* **NOT APPLICABLE** — Requirement does not apply to the current system.
* **NOT TESTED** — Verification has not yet been performed.

---

## 15. Evidence Requirements

Verification results should include sufficient evidence to reproduce or validate the conclusion.

Evidence may include:

* Command output
* Configuration state
* File permissions
* Group membership
* Sudo authorization
* Authentication or authorization logs
* Service state
* Network configuration
* Screenshots where appropriate

Sensitive information, credentials, private keys, tokens, and other secrets must not be committed to the repository.

---

## 16. Verification Record

Detailed results should be recorded during implementation and audit activities.

| Test ID | Result     | Evidence | Notes |
| ------- | ---------- | -------- | ----- |
| TC-001  | NOT TESTED | —        | —     |
| TC-002  | NOT TESTED | —        | —     |
| TC-003  | NOT TESTED | —        | —     |
| TC-004  | NOT TESTED | —        | —     |
| TC-005  | NOT TESTED | —        | —     |

Additional test results should be added as verification is performed.

---

## 17. Acceptance Criteria

The security baseline should not be considered verified until:

1. Required security controls have been tested.
2. Unauthorized access tests produce the expected denial.
3. Authorized operations remain functional.
4. No unexplained administrative privileges remain.
5. Security-relevant configuration is documented.
6. Test evidence is available for significant controls.
7. Failures and exceptions are documented and reviewed.
8. The final verification results are reflected in the audit report.

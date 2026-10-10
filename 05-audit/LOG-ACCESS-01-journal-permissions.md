# LOG-ACCESS-01 — System Journal Read Access

**Status:** Informational — Policy Review Required  
**Category:** Access Control / Least Privilege

## Observation

The `cyba56` account belongs to the `adm` group. The system journal file is owned by `root:systemd-journal` with permissions `640`. Its Access Control List (ACL) grants the `adm` group read access.

## Evidence

- **Journal file:** `/var/log/journal/1f76e61f06c84491ad8f80b9013a9297/system.journal`
- **File ownership and mode:** `root:systemd-journal`, `640`
- **User group membership:** `adm`
- **ACL:** `group:adm:r--`
- **Verification:** Successfully read one journal entry using `journalctl` without `sudo`.
- **System documentation:** The installed `base-passwd` documentation describes `adm` as a system-monitoring group whose members can read many log files under `/var/log`.

## Security Impact

Members of the `adm` group may be able to read operational logs containing information about system activity, services, and user sessions. The actual risk depends on the information recorded and the account's authorized responsibilities.

## Recommendation

Review `adm` group membership against the system's least-privilege policy. Confirm that each member requires log-reading access. Do not change group membership or ACLs until operational requirements have been assessed.

## Conclusion

The observed access is explained by the configured ACL and `adm` group membership. This assessment has not established a vulnerability or privilege-escalation path.

**Assessment type:** Read-only verification  
**Configuration changed:** No

# Kali Linux User Separation — Implementation & Verification Notes

**Project:** Kali Security Baseline Assessment  
**Date:** 10 October 2026  
**Scope:** Administrative separation, security practice, development, and legacy account restriction

## 1. Objective

Kali Linux system par separate user accounts establish karna, least privilege follow karna aur daily activities ko administrative privileges se isolate karna.

Defined account roles:

| Account | Role | Intended privilege |
|---|---|---|
| `admin` | System administration | Sudo access |
| `secuser` | Offensive security practice and pentesting | No sudo |
| `devuser` | Security tool development | No sudo |
| `cyba56` | Legacy/default account | Login disabled and supplementary privileges removed |

## 2. Administrative Account Verification

### Purpose
Confirm karna ki dedicated `admin` account system administration ke liye functional hai.

### Verification performed
```bash
sudo -v && sudo whoami
```

**Observed result:** `root`

Direct graphical login to `admin` bhi verify kiya gaya.

### Status
**Verified:** `admin` ke paas working sudo access hai.

## 3. Dedicated User Accounts

### Accounts identified
```text
admin
secuser
devuser
cyba56
```

### Account configuration observed
```text
admin:x:1002:1002::/home/admin:/bin/bash
secuser:x:1001:1001::/home/secuser:/bin/bash
devuser:x:1003:1003::/home/devuser:/bin/bash
cyba56:x:1000:1000:cyba56,,,:/home/cyba56:/bin/bash
```

Yeh initial configuration ka record hai; `cyba56` ka shell baad mein change kiya gaya.

## 4. `secuser` — Offensive Security Account

### Intended purpose
- Authorized penetration testing
- Security lab practice
- Offensive security tools ka use

### Verification performed
```bash
sudo -l
```

**Observed result:**
```text
Sorry, user secuser may not run sudo on kali.
```

Ek tool availability check bhi kiya gaya:
```bash
command -v subfinder
```

Us waqt koi path return nahi hua.

### Status
**Verified:** `secuser` ko normal sudo permission nahi mili.

**Pending:** Installed tools, file permissions aur additional privilege-escalation paths ka comprehensive review.

## 5. `devuser` — Development Account

### Intended purpose
- Security tools develop karna
- Scripts aur code maintain karna
- Development environment ko administrative account se separate rakhna

### Status
**Configured:** Dedicated `devuser` account maujood hai.

**Pending:** Current sudo policy, group memberships, writable system paths aur development tooling ki independent verification.

## 6. Security Baseline Repository Migration

### Purpose
Baseline repository ko legacy account ke home directory se dedicated administrative account ke home directory mein move/copy karna.

### Commands performed
```bash
sudo cp -a /home/cyba56/kali-security-baseline /home/admin/
sudo chown -R admin:admin /home/admin/kali-security-baseline
```

### Verification performed
```bash
git rev-parse --show-toplevel
git status --short --branch
git remote -v
```

Repository `/home/admin/kali-security-baseline` par verify hui.

Observed branch status:
```text
## main...origin/main
```

Remote:
```text
https://github.com/Mangal-Sec/kali-security-baseline.git
```

### Status
**Verified at the time of migration:** Repository admin-owned path par thi aur Git tracking configured thi.

**Note:** Original repository `/home/cyba56/` mein untouched chhodi gayi thi. Current status dobara verify nahi kiya gaya.

## 7. `cyba56` Password Lock

### Purpose
Legacy account ke password-based login ko block karna.

### Command executed
```bash
sudo passwd -l cyba56
```

### Verification
```bash
sudo passwd -S cyba56
```

Observed status:
```text
cyba56 L ...
```

`L` password-locked status ko indicate karta hai.

### Status
**Verified:** Password lock apply hua.

**Limitation:** Password lock apne aap public-key authentication ya har doosre authentication mechanism ko disable nahi karta.

## 8. `cyba56` Interactive Shell Disablement

### Command executed
```bash
sudo usermod --shell /usr/sbin/nologin cyba56
```

### Verification
```bash
getent passwd cyba56
```

Observed result:
```text
cyba56:x:1000:1000:cyba56,,,:/home/cyba56:/usr/sbin/nologin
```

### Status
**Verified:** Login shell `/usr/sbin/nologin` set hua.

Isse normal interactive shell login reject hona chahiye.

## 9. `cyba56` Account Expiration

### Command executed
```bash
sudo usermod --expiredate 1970-01-02 cyba56
```

### Verification
```bash
sudo chage -l cyba56
```

Observed result:
```text
Account expires : Jan 02, 1970
```

### Status
**Verified:** Account expiration date set hui.

Expired account ko PAM-based login paths aam taur par reject karte hain. Har service aur authentication method ka behavior separately test karna baaki hai.

## 10. `cyba56` Sudo Privilege Removal

### Command executed
```bash
sudo gpasswd -d cyba56 sudo
```

Observed result:
```text
Removing user cyba56 from group sudo
```

Verification:
```bash
id cyba56
```

Observed output mein `sudo` group nahi thi.

### Status
**Verified:** `sudo` supplementary group se removal successful hua.

## 11. All Supplementary Group Memberships Removed

Initial supplementary groups:
```text
adm
dialout
cdrom
sudo
audio
dip
video
plugdev
users
lpadmin
netdev
kaboxer
wireshark
```

### Command executed
```bash
sudo usermod -G "" cyba56
```

### Verification
```bash
id cyba56
```

Observed final output:
```text
uid=1000(cyba56) gid=1000(cyba56) groups=1000(cyba56)
```

### Status
**Verified:** `cyba56` ki saari supplementary group memberships remove ho gayi. Primary group `cyba56` preserve hui.

Isse `sudo`, `adm`, `lpadmin`, `wireshark` aur doosri listed groups ki group-based permissions remove hui.

## 12. Legacy Account — Consolidated State

| Control | Status |
|---|---|
| Password locked | Verified |
| Interactive shell set to `nologin` | Verified |
| Account expiration set | Verified |
| Sudo supplementary group removed | Verified |
| All supplementary groups removed | Verified |
| User account retained | Verified |
| Home directory preserved | No deletion command performed |
| Every authentication path blocked | Not yet comprehensively verified |

**Important:** `cyba56` ko delete nahi kiya gaya. Account ID, primary group aur home directory preserve karne ka intention tha.

## 13. Session Cleanup and Reboot

Login-session investigation ke dauran `cyba56` ka session `closing`/`abandoned` state mein tha aur kuch residual processes remaining the.

Machine reboot ke baad:
```bash
loginctl list-sessions
```

Observed sessions sirf `admin` ke the.

### Status
**Verified at that time:** Reboot ke baad `cyba56` ka active login session list mein nahi tha.

Yeh future login attempts ki failure ka proof nahi hai.

## 14. Remaining User Separation Verification

In controls ko abhi independently verify karna hai:

1. `admin` ka current sudo access.
2. `secuser` aur `devuser` ke current supplementary groups.
3. `secuser` aur `devuser` ke liye sudo policy aur direct sudoers rules.
4. `cyba56` ke SSH key, SFTP aur doosre service-specific authentication paths.
5. Legacy account ke owned files, scheduled jobs aur services par impact.
6. `cyba56` ke home directory aur sensitive files ki permissions.
7. Reboot ke baad current account/session state.

## 15. Security Assessment Conclusion

Initial user separation architecture establish ki gayi:

- `admin`: system administration.
- `secuser`: offensive security practice.
- `devuser`: development.
- `cyba56`: restricted legacy account.

`cyba56` ke password lock, `nologin` shell, expired account aur supplementary group removal ko command outputs se verify kiya gaya.

Lekin overall user separation ko **fully passed** declare karna abhi sahi nahi hoga. `secuser`, `devuser`, service-specific authentication aur direct privilege paths ka remaining verification complete karna hoga.

**Assessment status:** Partially implemented and partially verified.

# 01 - Enumeration (LDAP & Basic Host Discovery)

**Author:** Your Name  
**Date:** 2025-10-26  
**Target:** 192.168.56.5 (Windows Domain Controller)  
**Scope:** Internal lab exercise (GRCLAB)  
**Purpose:** Confirm LDAP reachability, domain naming contexts, and perform authenticated bind attempts to determine enumeration capability.

---

## Summary / Findings (high level)
- LDAP (port 389) is reachable and responds to an anonymous base query: `namingContexts` contains `DC=grclab,DC=local` etc.
- Authenticated SIMPLE bind attempt failed with `ldap_bind: Invalid credentials (49)` plus AD sub-code `data 52e` (bad credentials).
- Next steps: try UPN formatting, LDAPS/StartTLS if required, or Kerberos (GSSAPI) bind.

---

## Evidence index
| # | Item | File / Screenshot |
|---|------|-------------------:|
| 1 | Anonymous base query `namingContexts` | `Screenshots/<img width="712" height="413" alt="image" src="https://github.com/user-attachments/assets/295390e3-450a-415e-90c5-4dd6bd827c45" />
` |
| 2 | Authenticated bind failure (49 / data 52e) | `<img width="1323" height="158" alt="image" src="https://github.com/user-attachments/assets/0a57bed8-fe8d-4804-8ec3-0debb833f946" />
` |
| 3 | Full ldapsearch raw output | `Evidence/01-enum-ldap-output.txt` |

---

## Environment & prerequisites
- Kali Linux VM (host) — `ip a` shows `ethX` configured.
- Target DC: 192.168.56.5.
- Tools used: `ldapsearch` (OpenLDAP client), `nmap`, `ping`.
- All commands executed locally in a lab environment; no production credentials were used.

---

## Commands executed (recorded)

### 1) Basic reachability
```bash
# ping the host
ping -c 3 192.168.56.5

# 01 - Enumeration (Kerberos / LDAP / SPN discovery)

**Goal:** discover domain basics, SPNs (service accounts) and accounts that may allow AS-REP roasting.

**Prerequisites**
- Kali VM with network access to the target DC (e.g. `192.168.56.5`)
- Tools: `impacket` (GetNPUsers.py, GetUserSPNs.py), `ldap-utils` (optional), `nmap`
- Windows DC where you can read Security logs (or Wazuh collecting them)

> If you don't have `impacket` installed: `sudo apt update && sudo apt install -y python3-impacket` (or install via pip).

---

## 1. Network discovery / confirmation
From Kali:
```bash
# quick host check
ping -c 3 192.168.56.5

# port scan to confirm LDAP / Kerberos
sudo nmap -Pn -sS -sV -p 53,88,135,139,389,445,464,593,3268,5985 192.168.56.5 -oN nmap/initial-192.168.56.5.txt


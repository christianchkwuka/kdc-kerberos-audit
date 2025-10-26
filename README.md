# kdc-kerberos-audit

**Author:** christianchkwuka  
**Scope:** Lab Active Directory / Kerberos audit (enumeration → AS-REP → Kerberoast → detection)  
**Purpose:** Professional, repeatable playbook for auditing Kerberos in an AD lab. All steps are intended for authorized testing only.

dc-kerberos-audit/
├─ README.md
├─ docs/
│ ├─ 01-enumeration.md
│ ├─ 02-asrep-roast.md
│ ├─ 03-kerberoast.md
│ └─ 04-detection-wazuh.md
├─ scripts/
│ ├─ run-kerberoast.sh
│ └─ add-wazuh-rules.sh
├─ screenshots/
│ ├─ 01-enum-ldap.png
│ ├─ 02-asrep-4768.png
│ ├─ 03-kerberoast-4769.png
│ └─ 04-wazuh-alert.png
└─ evidence/
├─ tickets/
└─ cracked/




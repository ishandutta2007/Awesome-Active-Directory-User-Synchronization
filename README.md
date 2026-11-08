# Awesome-Active-Directory-User-Synchronization

# Awesome-Active-Directory-User-Synchronization

**Top Active Directory User Synchronization (Opensource) 🌟 Star if you like it! 🌟**



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on Hybrid Identity Sync, Directory Bridging, SCIM Provisioning & Self-Hosted Synchronization Engines*

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Active Directory & User Synchronization**. These tools enable organizations to keep user identities consistent across on-premises Active Directory, cloud directories (Entra ID, Okta, Google Workspace), and downstream applications—from fully managed sync agents with password hash synchronization to open-source engines that give teams control over their identity data flows.



**Examples** include Microsoft Entra Connect Sync, Okta AD Agent, JumpCloud AD Sync, Freshworks Directory Services, Ping Identity, OneLogin, Google Cloud Directory Sync, ForgeRock, and CyberArk (the category leaders in commercial space).



**Open-source emphasis**: This section is expanded with every relevant project for self-hosted AD synchronization, LDAP bridging, and open identity provisioning. **Critical note**: The open-source landscape is anchored by **LSC (LDAP Synchronization Connector)**—the BSD-licensed Java engine for continuous sync from databases, files, or LDAP to any LDAP directory, with Active Directory-specific functions for password updates and account status . **Apache Directory Studio** provides LDAP administration, and **bureaucrat** handles configuration file sync from LDAP. No open-source project matches Entra Connect's password hash sync or Okta's delegated authentication at enterprise scale, but for directory-to-directory sync, the options are production-proven.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **Microsoft Entra Connect Sync**

  **Hybrid identity synchronization** between on-premises AD and Entra ID. **Features**: **Password hash synchronization** (PHS); **pass-through authentication** (PTA); **federation with AD FS**; **device writeback**; **directory extensions** for custom attributes; **declarative provisioning** rules; **prevent accidental deletion**; scheduler for import/sync/export cycles . **Critical note**: Microsoft is **replacing Connect Sync with Cloud Sync**—Connect Sync will be retired once Cloud Sync reaches full feature parity. Cloud Sync uses the Entra provisioning agent instead of the Connect application . **Pricing**: Free with Entra ID; P1/P2 for advanced features. **Free tier**: Yes, core sync free. **Best for**: Microsoft-centric organizations needing hybrid identity—**trade-off**: plan for Cloud Sync migration; Connect Sync is being deprecated.



- **Okta AD Agent**

  **On-premises agent** for integrating Okta with Active Directory. **Features**: **Delegated authentication**—users authenticate against AD but access Okta-managed apps; **user provisioning and de-provisioning**; **import AD users and groups into Okta**; **password sync**; **group push** and **attribute writeback** . **Pricing**: Requires Okta subscription; agent is free. **Free tier**: Developer edition available. **Best for**: organizations wanting Okta as the identity plane while keeping AD as the credential store—**trade-off**: requires Okta subscription; agent runs on Windows Server.



- **JumpCloud AD Sync (ADI)**

  **Directory synchronization** between JumpCloud and Active Directory. **Features**: **One-way (AD → JumpCloud)** or **two-way** sync; **configurable sync group** for organizing managed AD groups; **advanced dissociation management**—Remove, Disable, or Retain users when disconnected; **account unlock status sync**; **nested group sync control** (Minimal/Inheritance or Match/Mirroring) . **Pricing**: Included with JumpCloud subscription. **Free tier**: Yes, up to 10 users. **Best for**: JumpCloud users wanting AD integration without full migration—**trade-off**: requires JumpCloud subscription; agent runs on Windows Server.



- **Freshworks Directory Services (Orch)**

  **Active Directory orchestration** within Freshworks workflows. **Features**: **User management**—create, delete, get, update, disable/enable, reset password, unlock account, move to another OU; **group management**—create, delete, get, check membership; **computer management**—delete, disable, enable, get OU; **object management**—move object by GUID . **Pricing**: Included with Freshworks subscriptions. **Free tier**: Limited. **Best for**: Freshworks customers wanting AD actions within support workflows—**trade-off**: orchestration actions, not continuous directory sync.



- **Google Cloud Directory Sync (GCDS)**

  **Directory synchronization** from AD/LDAP to Google Workspace. **Pricing**: Free with Google Workspace. **Free tier**: Included with Workspace. **Best for**: Google Workspace organizations syncing users and groups from AD—**trade-off**: sync tool, not a standalone directory; one-way sync.



- **Ping Identity / ForgeRock**

  **Enterprise identity platform** with AD integration and federation. **Features**: ForgeRock AM supports **identity linking and bulk federation** between IdP and SP; **persistent vs. transient federation**; **ssoadm bulk federation commands** for mapping local to remote user IDs . **Pricing**: Quote-only. **Free tier**: None. **Best for**: regulated enterprises needing federation and directory integration—**trade-off**: requires identity engineering expertise.



- **OneLogin**

  **Cloud IAM** with AD integration. **Pricing**: Quote-only; tiered by users. **Free tier**: Trial available. **Best for**: mid-market organizations wanting straightforward directory and SSO.



- **CyberArk Identity**

  **Identity security** with directory integration and privileged access. **Pricing**: Quote-only. **Free tier**: None. **Best for**: enterprises prioritizing privileged access alongside directory sync.



## Open-Source GitHub Projects



- **LSC (LDAP Synchronization Connector)**

  **Open-source directory synchronization engine** (BSD) — **the most complete open-source tool for AD synchronization**, designed to sync any data source to an LDAP directory with Active Directory-specific functions . **Features**: **Multiple connectors**—any LDAPv3 server, databases via JDBC, flat files; **continuous sync** or one-shot import; **three update policies**—forcing values, non-destructive, merging; **script engine** (JavaScript/Groovy) for attribute manipulation; **AD-specific libraries**—password update (unicodePwd), account status manipulation (userAccountControl), unused account detection (lastLogonTimestamp); **detailed logging** in LDIF and CSV; **Nagios monitoring plugin**; **graphical setup wizard** (optional) . **Tech stack**: Java. **Deploy**: Self-hosted (Java, any platform). **Trade-off**: **Configuration-driven**—requires understanding of XML/JSON config and scripting; not a point-and-click tool. **Best for**: organizations needing reliable, scriptable AD-to-LDAP or database-to-AD synchronization—especially those with custom attribute mapping or complex transformation requirements.



- **bureau**

  **Centralized configuration agent for LDAP** (Go, MIT) — **the most focused open-source tool for LDAP-driven configuration sync**, useful for directory-driven infrastructure automation . **Features**: **RFC-compliant**—works with OpenLDAP, Active Directory, 389 DS; **customizable schemas** with globally valid OIDs and modifiable templates; **host-specific entries** under `cn=<hostname>,<base>`; **in-memory change tracking** for efficient polling; **daemon mode** with systemd integration; **built-in schemas** for keepalived and config files . **Tech stack**: Go. **Deploy**: Self-hosted (binary, systemd). **Trade-off**: **Configuration files only**—not user/group synchronization; designed for infrastructure config, not identity provisioning. **Best for**: teams wanting to drive server configuration from LDAP—especially those managing fleets with keepalived or similar services.



- **Windows-to-Samba Migration Scripts**

  **PowerShell/Bash scripts for AD user migration** (open source) — **the most practical open-source tool for migrating users between AD and Samba AD** . **Features**: **Export from source AD**—PowerShell script retrieves users from specified OU, gathers properties (SamAccountName, GivenName, Surname, Mail, Department), resolves group memberships, exports to CSV; **Import to target Samba AD**—Bash script reads CSV, creates OUs, creates/updates users with passwords, sets password expiry, adds to groups; **supports bulk creation** and replication between Samba instances . **Tech stack**: PowerShell, Bash. **Deploy**: Run export on Windows (RSAT), import on Linux (samba-tool). **Trade-off**: **One-time migration**—not continuous synchronization; requires manual CSV transfer. **Best for**: organizations migrating from Windows AD to Samba AD or replicating between Samba domains—not for ongoing hybrid sync.



### Additional Strong Open-Source Options



- **Apache Directory Studio** — LDAP directory editor and browser (Apache 2.0). **Note**: **Administration tool, not sync engine**—for browsing and editing LDAP, not continuous synchronization. **Best for**: LDAP administrators needing a GUI for directory management.

- **python-ldap / ldap3** — Python LDAP libraries (open source). **Note**: **Building blocks**—for developers writing custom sync scripts, not a ready-made sync tool. **Best for**: developers building bespoke AD synchronization pipelines.

- **No mature open-source AD-to-cloud sync platform exists.** Entra Connect, Okta AD Agent, and JumpCloud ADI dominate. **LSC** provides directory-to-directory sync but not cloud provisioning. For hybrid identity at enterprise scale, commercial platforms are required.



**Frameworks for building custom systems**: **LSC** is the strongest open-source starting point for scriptable AD synchronization, with AD-specific password and account status functions . **bureau** fills a niche for LDAP-driven config. **Windows-to-Samba scripts** handle migration but not ongoing sync. **None match Entra Connect's password hash sync or Okta's delegated authentication.**



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, license (for open-source), and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Directory synchronization platforms handling credentials must comply with data protection regulations (GDPR, CCPA, etc.) and implement appropriate access controls.

- **The "hybrid identity sync" vs. "directory orchestration" vs. "migration script" vs. "config sync" distinction is critical.** **Entra Connect, Okta AD Agent, and JumpCloud ADI** are **hybrid identity sync**—they synchronize users, passwords, and groups between AD and cloud directories . **Freshworks Orch** is **directory orchestration**—it performs AD actions within workflows, not continuous sync . **Windows-to-Samba scripts** are **migration**—one-time transfer, not ongoing sync . **LSC** is **directory-to-directory sync**—it moves data from any source to LDAP, with AD-specific functions . **bureau** is **config sync**—it pushes configuration files from LDAP, not user identities . **Choose based on whether you need ongoing identity sync, workflow actions, migration, or infrastructure config.**

- **Microsoft Entra Connect Sync is being replaced by Cloud Sync.** Microsoft states Cloud Sync will replace Connect Sync once feature parity is reached; Connect Sync will be retired . **Plan your migration before deploying new Connect Sync instances.**

- **LSC is the most capable open-source AD sync engine**—BSD licensed, with AD-specific password (unicodePwd) and account status (userAccountControl) functions, plus scripting for custom transformations . **The trade-off**: configuration-driven; requires Java and XML/scripting expertise.

- **JumpCloud ADI's two-way sync** is unique among the commercial options—AD → JumpCloud or AD ↔ JumpCloud, with granular dissociation controls (Remove/Disable/Retain) and nested group sync policies . **The trade-off**: requires JumpCloud subscription.

- **Freshworks Directory Services is orchestration, not sync.** It performs AD actions (create user, reset password, move OU) within Freshworks workflows—it does not continuously synchronize users between systems . **Do not confuse it with a sync agent.**

- **Windows-to-Samba scripts are for migration, not sync.** They export from AD to CSV, then import to Samba—a one-time operation requiring manual transfer . **For ongoing sync between AD and Samba, you need a different tool.**

- Self-hosted open-source solutions require proper infrastructure (Java for LSC, Go for bureau), security hardening, and ongoing maintenance. **Directory sync tools handle credentials and identity data**—ensure your deployment meets your organization's security and compliance requirements before synchronizing production identities.



---



**Made for identity architects, system administrators, and organizations building transparent directory synchronization solutions.**

Let's make Active Directory & User Synchronization more open, data-driven, and identity-aware.

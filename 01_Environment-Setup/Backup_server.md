# Backup server
A [backup server](https://novoserve.com/blog/backup-server-is-essential-for-your-business-continuity) works as an isolated data vault. It pulls or receives copies of production data, deduplicates it to save space, compress it, encrypts it, and stores it across a retention timeline. 

#### Working steps
```
[ Production Server ] ---> (1. Data Pull / Push via Agent) ---> [ Backup Server ]
                                                                       |
                                                           (2. Deduplicate & Compress)
                                                                       |
                                                           (3. Encrypt at Rest)
                                                                       |
                                                           (4. Apply Retention Policy)
                                                                       |
                                                           (5. Offsite Replication)
```

### Why we need dedicated server

- Disaster recovery: If production hardware catches fire, suffers a motherboard failure, or experiences a corrupted filesystem, business can recover because the data lives safely on separate physical disks.

- Protection Against Ransomware: Production server are internet-facing and vulnerable to malware. A dedicated backup server can be structured with immutable storage, meaning once a data is written, even a compromised production administrator can not delete or encrypt it.

- Point-in-Time recovery: If a bad code update silently corrumpts active production database on Tuesday, a backup server allows to roll back specifically to Monday inghts uncorrupted state.

## Some popular backup server OS

### 1. Red Hat Enterprise Linux (REHL)
Using REHL as a dedicated bacup server is an excellent, enterprise-grade choice. It can run on 2 GB RAM and 10 GB disk space is enough for installation, But recommended specification is 4GB and 30 GB.

 Full support concludes on May 31, 2027. Maintenance support extends until May 31, 2032. An optional Extended Life Cycle Support (ELS) add-on is available until May 31, 2035.

#### Security Status
Includes OpenSSL 3.0, enhanced system-wide crypto-policies (disabling outdated protocols like TLS 1.0/1.1, DTLS 1.0, RC4, and increasing minimum RSA key sizes), and protection against [hardware-level vulnerabilities](https://medium.com/@sampaththaranga/hardware-vulnerabilities-the-hidden-risk-in-your-devices-11102f980312) such as Spectre and Meltdown.

They Provides
1. Instant security patchum
2. Advanced native security hardening
3. Long-term predictability lifecycle
4. Broad vendor software capability


### 2. Alma Linux 9

Is completely free, open-source enterprise linux distribution managed by the community-driven AlmaLinux OS Foundation. It was created as a direct response to Red Hat discontinuing the traditional stable CentOS format.
Requires only 1.5 GB RAM for minimal installation and 4 GB for graphical Installation. The recommended disk space is 30 GB. 

 Active support is guaranteed until May 31, 2027, with security support extending to May 31, 2032

#### Security status
Includes Errata for security advisories, GPG keys for package verification, OpenSCAP and OVAL for security compliance auditing, Software Bill of Materials (SBOM) for supply chain security, and Secure Boot support. It also features Security-Enhanced Linux (SELinux) for mandatory access control, Firewalld for network protection, Fail2ban for intrusion prevention, AIDE for file integrity monitoring, and an Audit daemon for logging security-relevant events. SSH root login is disabled by default, and customizable TLS/SSL encryption settings are available in Rsyslog.

Advantages:

1. Zero subscription management or registration
2. 1:1 Binary compatibility
3. Hyper fast security patching
4. Absolute predictability and longevity

Disadvantages:

1. Lacks direct vendor certification
2. No commercial help desk



Other Pupular Bacup server OS

[+] Proxmox Backup Server (PBS)  : If production environment uses virtual machines, PBS is an industry favourite.

[+] TrueNAS SCALE or Core : Worlds most popular dedicated storage operating system.

[+] Ubuntu Server LTS (Long Term Support): If you want a standard, versatile, linux distro instead of Red Hat clone, Ubuntu LTS is the global standard.

## Conclusion

Although we can use any linux distro as backup servers because all the distros has the required tools for backup, yet we should not use them because of some reasons like 
- Rolling releases
- Desktop focused
- Short life


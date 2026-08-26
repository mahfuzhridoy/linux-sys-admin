# Backup Server

A [backup server](https://novoserve.com/blog/backup-server-is-essential-for-your-business-continuity) works as an isolated data vault. It pulls or receives copies of production data and stores them separately from the production environment.

Depending on the backup software, the backup server may perform **incremental backups, deduplication, compression, encryption, integrity verification, and retention management**. It can also replicate backup copies to an offsite or secondary location.

The main purpose of a backup server is not simply to make another copy of data. It is to provide **reliable recovery points** that can be used when production data is lost, corrupted, accidentally deleted, or affected by a security incident.

## Working steps

```text
[ Production Server ]
          |
          | (1) Data Pull / Push via Agent
          v
[ Backup Server ]
          |
          | (2) Incremental Backup
          |     + Deduplicate & Compress
          v
[ Backup Storage ]
          |
          | (3) Encrypt in Transit / At Rest
          v
[ Retention Policy ]
          |
          | (4) Keep Multiple Recovery Points
          v
[ Offsite / Secondary Backup ]
          |
          | (5) Replication
          v
[ Disaster Recovery Location ]
```

The exact order of deduplication, compression, and encryption can vary depending on the backup software being used.

### Additional backup considerations

* **Incremental Backup:** Only data that has changed since a previous backup is transferred or stored, reducing storage requirements and network traffic.
* **Deduplication:** Identifies duplicate blocks or chunks of data so that the same information does not need to be stored repeatedly.
* **Compression:** Reduces the amount of storage space required.
* **Encryption:** Protects backup data both while it is being transferred and while it is stored.
* **Integrity Verification:** Checks whether backup data has become corrupted or modified.
* **Retention Policy:** Defines how long daily, weekly, monthly, or other recovery points should be kept.
* **Offsite Replication:** Keeps another copy in a different physical or logical location so that a disaster affecting the primary site does not destroy both production and backup data.
* **Restore Testing:** A backup is useful only if it can actually be restored. Regular test restores should therefore be performed.

## Why we need dedicated server

### Disaster recovery

If the production server catches fire, suffers a motherboard or disk failure, experiences filesystem corruption, or is otherwise destroyed, the business can recover because the data is stored separately on another system.

Keeping the only backup on the same physical server as the production data does not provide meaningful protection against complete server failure.

### Protection Against Ransomware

Production servers are often exposed to users, applications, and networks and may be vulnerable to malware or ransomware.

A dedicated backup server can provide an additional security boundary. It can be configured with network isolation, separate credentials, restricted administrative access, and **immutable storage**.

Immutable storage means that backup data cannot be modified or deleted during its protected retention period. This can help prevent an attacker who compromises the production environment from deleting or encrypting the available recovery points.

However, simply having a dedicated backup server does **not automatically protect against ransomware**. The backup infrastructure itself must also be properly secured.

### Point-in-Time recovery

If a bad code update silently corrupts an active production database on Tuesday, the latest backup may also contain the corrupted data.

By maintaining multiple recovery points, a backup server can allow administrators to restore the database to an earlier known-good state, such as Monday night's backup.

This is called **point-in-time recovery**.

### Backup verification and restore testing

A backup job showing **"Successful"** does not always mean that the data can actually be recovered.

Backup systems should periodically verify the integrity of stored data and perform test restores.

The important question is not only:

> "Did the backup complete?"

but also:

> "Can we successfully restore from it?"

### RPO and RTO

Two important concepts in backup and disaster recovery are:

**RPO — Recovery Point Objective**

Defines how much data the organization can afford to lose.

For example, an RPO of 24 hours may mean that losing up to one day's worth of data is acceptable.

**RTO — Recovery Time Objective**

Defines how quickly the system or service needs to be restored after a failure.

For example, an RTO of 4 hours means the organization expects the service to be restored within four hours.

Therefore, backup planning is not only about **where data is stored**, but also about **how much data can be lost and how quickly it must be recovered**.

## Some popular backup server OS

### 1. Red Hat Enterprise Linux (RHEL)

Using RHEL as a dedicated backup server is an excellent enterprise-grade choice when an organization requires commercial vendor support, predictable lifecycle management, strong security controls, and broad enterprise software compatibility.

RHEL can run with relatively modest resources for a minimal installation, although the actual hardware requirements for a backup server depend much more on the **backup workload, storage capacity, deduplication/compression requirements, and number of clients** than on the minimum OS installation requirements.

RHEL 9 follows Red Hat's long-term lifecycle model, with support extending for many years. The exact support dates depend on the RHEL version and support phase, so administrators should always check Red Hat's current lifecycle documentation before planning an upgrade or deployment.

#### Security Status

RHEL provides several security features that are useful for backup infrastructure, including:

* SELinux for mandatory access control
* System-wide cryptographic policies
* Regular security updates and errata
* Firewall management
* Audit logging
* Package signing and verification
* Security and compliance tooling
* Support for modern cryptographic libraries and protocols
* Security hardening capabilities

It also provides mechanisms for reducing the risk from outdated protocols and weak cryptographic configurations.

They provide:

1. Regular security patches
2. Advanced native security hardening
3. Long-term and predictable lifecycle
4. Broad enterprise software compatibility
5. Commercial vendor support
6. Extensive documentation and certification ecosystem

### 2. AlmaLinux 9

AlmaLinux is a free, open-source enterprise Linux distribution managed by the community-driven AlmaLinux OS Foundation.

It provides a RHEL-compatible environment and is a popular choice for organizations that want an enterprise Linux platform without requiring a RHEL subscription for the operating system itself.

AlmaLinux 9 has a long support lifecycle, with security support extending to **May 31, 2032** according to the AlmaLinux lifecycle information.

The actual hardware requirements depend on the installation type and workload. A minimal installation can run with relatively little RAM, while a dedicated backup server will normally require significantly more resources depending on the amount of data being processed and stored.

#### Security status

AlmaLinux provides several security capabilities suitable for a dedicated backup server, including:

* Security errata and updates
* GPG keys for package verification
* SELinux for mandatory access control
* OpenSCAP and OVAL security/compliance tooling
* Secure Boot support
* Firewalld for network protection
* AIDE for file integrity monitoring
* Audit daemon for security-related logging
* SSH-based remote administration
* Configurable TLS/SSL security

Advantages:

1. Free and open-source
2. No mandatory subscription for the operating system
3. RHEL-compatible ecosystem
4. Long security-support lifecycle
5. Familiar enterprise Linux administration tools
6. Strong security features
7. Suitable for organizations that want an enterprise Linux environment without RHEL licensing costs

Disadvantages:

1. No direct Red Hat vendor support
2. Some third-party software vendors may officially certify RHEL but not AlmaLinux
3. Commercial support may require a separate support provider
4. Administrators are responsible for ensuring that the complete backup stack is supported and maintained

## Other Popular Backup server OS

[+] **Proxmox Backup Server (PBS):** If the production environment uses Proxmox VE and virtual machines, PBS is a purpose-built backup platform and an excellent choice. It supports incremental backups, deduplication, compression, encryption, integrity verification, remote synchronization, and backup verification.

[+] **TrueNAS:** TrueNAS is a storage-focused operating system/platform built around ZFS. It is useful when the primary requirement is a reliable storage repository with features such as snapshots, replication, SMB/NFS, and storage management. However, a NAS by itself should not be considered a complete backup strategy.

[+] **Ubuntu Server LTS (Long Term Support):** If you want a standard, versatile Linux distribution instead of an RHEL-compatible distribution, Ubuntu Server LTS is a strong choice. It has a large software ecosystem, extensive documentation, long-term support releases, and broad compatibility with backup applications.

## Important point: RAID is not a backup

RAID can protect against certain types of disk failure, but it does not protect against:

* Accidental deletion
* Ransomware
* Filesystem corruption
* Incorrect administrator actions
* Application-level data corruption
* Fire, flood, or other physical disasters

Therefore:

> **RAID is not a backup.**

RAID may be useful inside a backup server to improve storage availability or protect against certain disk failures, but independent backup copies are still required.

## 3-2-1 Backup Rule

A commonly used backup principle is the **3-2-1 rule**:

* **3** copies of important data
* **2** different types of storage/media
* **1** copy stored offsite

For stronger protection against ransomware and other destructive events, organizations may use variations such as **3-2-1-1-0**, which adds an offline or immutable copy and emphasizes verified, error-free backups.

## Conclusion

Although we can use many Linux distributions as backup servers because Linux provides the required tools for storage, networking, encryption, scheduling, and backup software, we should not select a distribution only because it can technically run backup software.

For a critical backup server, we should prefer a platform that provides:

* Long-term support
* Predictable updates
* Strong security features
* Minimal unnecessary services
* Good hardware and software compatibility
* Reliable storage support
* A clear upgrade path
* Good backup-software support

We should generally avoid using:

* **Rolling-release distributions** for critical backup infrastructure because frequent package changes can reduce predictability.
* **Desktop-focused distributions** because they include unnecessary software and services for a dedicated server.
* **Short-life distributions** because they require more frequent migrations and maintenance.
* **Unsupported or obsolete distributions** because they may no longer receive security updates.

However, the **operating system alone does not make a backup system reliable or secure**.

A proper backup strategy should also include:

* Separate or isolated backup storage
* Appropriate retention policies
* Encryption
* Multiple recovery points
* Integrity verification
* Immutable or offline copies where appropriate
* Offsite replication
* Monitoring and alerting
* Regular restore testing
* Clearly defined RPO and RTO

The main lesson is:

> **Having a backup is not the same as having a recovery strategy.**

A good backup server should therefore be treated as an important part of the organization's **disaster recovery and security infrastructure**, not simply as another storage server.

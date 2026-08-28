# Production Server

A **production server** is the main server environment where applications, websites, databases, or services run and provide services to actual users.

Unlike a backup server, which mainly stores recovery copies of data, a production server handles the **active workload** of the organization.

Depending on the environment, a production server may run:

* Web applications
* Databases
* APIs
* Business applications
* Virtual machines
* File services
* Authentication services

The main purpose of a production server is to provide **stable, secure, and reliable services** to users.

## Working steps

```text
[ Users / Clients ]

          |

          | (1) Request

          v

[ Production Server ]

          |

          | (2) Process Application / Service

          v

[ Application / Database ]

          |

          | (3) Store / Retrieve Data

          v

[ Storage System ]

          |

          | (4) Backup Data

          v

[ Backup Server ]
```

The exact architecture can vary depending on the organization. Some environments may separate the web server, application server, database server, and storage server.

## Important production server considerations

* **Security:** The server should be protected with proper access control, firewall rules, security updates, and secure authentication.

* **Availability:** Production services should remain available as much as possible. Critical systems may require redundancy or high-availability configurations.

* **Performance:** CPU, RAM, storage, and network resources should be sufficient for the expected workload.

* **Monitoring:** Administrators should monitor CPU usage, memory, disk space, network activity, service status, and system logs.

* **Regular Updates:** Security patches and important updates should be applied carefully and preferably tested before deployment.

* **Backup:** Production data should be backed up regularly to a separate backup system.

## Why do we need a dedicated production server?

### Reliability

A dedicated production server provides a controlled environment for running important applications and services.

Unnecessary software and services should be avoided because they can consume resources and increase the attack surface.

### Security

Production servers often contain important business data and provide services to users.

They should therefore use:

* Restricted administrative access
* Strong authentication
* Firewall protection
* Regular security updates
* Secure remote access
* Logging and monitoring
* Proper permission management

### Performance

Running production workloads on a properly configured server helps ensure that applications receive sufficient CPU, memory, storage, and network resources.

For larger workloads, services may be distributed across multiple servers.

### Separation from Backup Infrastructure

The production server and backup server should normally be treated as separate systems.

If both production data and the only backup are stored on the same server, a major server failure or security incident could affect both.

Therefore:

> **The production server runs the active workload, while the backup server protects recovery copies.**

## High Availability

For critical services, a single production server can become a **single point of failure**.

Organizations may use multiple servers with technologies such as:

* Load balancing
* Failover
* Replication
* Clustering
* Redundant storage

Example:

```text
                 [ Users ]

                     |

                     v

               [ Load Balancer ]

                 /           \

                v             v

     [ Production Server 1 ] [ Production Server 2 ]

                \             /

                 v           v

                  [ Database ]
```

This can improve availability if one server experiences a failure.

## Monitoring and Maintenance

A production server should be regularly monitored for:

* CPU usage
* Memory usage
* Disk space
* Disk health
* Network activity
* Service availability
* System logs
* Failed login attempts

Monitoring helps administrators identify problems before they cause major service interruptions.

## Some popular production server OS

### 1. Red Hat Enterprise Linux (RHEL)

RHEL is a strong choice for enterprise production servers.

It provides:

1. Long-term and predictable lifecycle
2. Regular security updates
3. Strong security features
4. Broad enterprise software compatibility
5. Commercial vendor support
6. Enterprise management tools

It is commonly used for business applications, databases, web servers, and other critical workloads.

### 2. AlmaLinux

AlmaLinux is a free and open-source enterprise Linux distribution with a RHEL-compatible environment.

Advantages:

1. Free and open-source
2. Enterprise-focused platform
3. Long support lifecycle
4. Strong security features
5. Familiar Linux administration tools
6. Good compatibility with many server applications

It can be a good choice for organizations that want an enterprise-style Linux environment without requiring a RHEL subscription.

### 3. Ubuntu Server LTS

Ubuntu Server LTS is another popular choice for production servers.

It provides:

* Long-term support releases
* Large software ecosystem
* Extensive documentation
* Broad cloud compatibility
* Strong community and commercial support options

It is commonly used for web servers, cloud infrastructure, containers, and application hosting.

## Important point: Production is not Backup

A production server may use RAID, redundant disks, snapshots, or replication, but these do not automatically replace a proper backup strategy.

For example, RAID does not protect against:

* Accidental deletion
* Ransomware
* Application-level data corruption
* Incorrect administrator actions
* Major physical disasters

Therefore:

> **High availability is not the same as backup.**

A production system can remain available while still having corrupted data. Independent backups are still necessary.

## Conclusion

A production server is the environment responsible for running the organization's active applications and services.

For a critical production server, we should prefer a platform that provides:

* Stability
* Long-term support
* Regular security updates
* Good hardware compatibility
* Strong security features
* Reliable performance
* Monitoring and logging
* A clear maintenance and upgrade path

The operating system alone does not make a production environment reliable.

A proper production infrastructure should also include:

* Security hardening
* Monitoring and alerting
* Regular maintenance
* Backup systems
* Access control
* Capacity planning
* Disaster recovery planning

The main lesson is:

> **A production server is designed to keep services running, while a backup server is designed to help recover when things go wrong.**

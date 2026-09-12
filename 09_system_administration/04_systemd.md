# Systemd
Most modern linux systems uses systemd as the default init system in service manager. Its name comes from system management daemon. It is a linux initialization and a service manager with many components such as on demand service management, logging, boot manager etc.

It start while booting the system.

## Phases of booting linux

1. First step: the system powers up
2. The bootloader (GRUB) loads the kernel
3. Then the kernel loads initial RAM disk that loads the system drives and looks for the root file system
4. Once the kernel, it begins the systemd initialization system. 
5. systemd starts with the process_id 1 as the first process then takes over and then continues to mount the hosts file systems and starts services

#

To see Systemd version: `systemd --version` 

To see Boot process time: `systemd --analyze`

To list all running units ordered by initializing time: `systemd analyze blame`


Systemd introduces the concepts of systemd units such as: service unit, mount unit, socket unit, and slice unit. They are defined in unit configuration files which include informations about the unit type and its behavior. For service management tasks the unit file contains instructions about how to start stop or restart a service.

#

To control systemd system and service manager `systemctl` command is used. This is very common for sysadmin jobs.

## Operations on services
There are some operations to manage services which is done by `systemctl`. The operations include:

> Note: All the commands should be run with sudo command. service name does not need to add the suffix '.service'.

- **Checking status:** To check service status, `systemctl status [service name]`. example command: `systemctl status nginx`.

- **Starting a service:** To start a service, `systemctl start [service name]`. example command: `systemctl start nginx`. The service will show active on status.

- **Stopping a service:**  To stop a service, `systemctl stop [service name]`. example command: `systemctl stop nginx`. The service will show inactive on status after this.

- **Restarting a service:** To restart a service, `systemctl stop [service name]`. example command: `systemctl stop nginx`. 

> The changed server configuration only take action after restarting the service. 

- **Reloading a service:** To restart a service, `systemctl reload [service name]`. example command: `systemctl reload nginx`. This is useful when a service does not need to restart to effect the changed configuration.

- **reload-or-restart:** When not sure if the service need to restart or reload to take actions, `systemctl reload-or-restart nginx` command can be used.

#

To configure a  service to start or not start at the booting time, there are two commands. Those are `enable` and `disable`. Enabled services starts at the booting time, disabled services never start automatically. They needs to be started manually with the start command. 

A service may be inactive at the current session but enabled at the same time. This service will auto start during next bootup.

Respective commands for enabling or disabling a service are, `systemctl enable [service name]` and `systemctl disable [service name]`

To check if the service will automatically start at the booting time `is-enabled` option is used.

# 

To prevent a service from being started both automatically or manually, the service can be set to masked. If a service is masked, the start or enable command wont work on that service.
To be able to use those command again, the service needs to be unmasked.

To mask or unmask a service, following commands are used:

- `systemctl mask nginx`. This will mask the nginx service.
- `systemct unmask nginx`. This will unmask the nginx service.

#

### Listing the services

To list all the active units that systemd knows about, `systemctl list-units` command is used. And to list all the units that systemd loaded regardless they are currently active or not `--all` option is used with them.
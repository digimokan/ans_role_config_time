# ans-role-config-time

Configure system clock, time, and time zone.

[![Release](https://img.shields.io/github/release/digimokan/ans-role-config-time.svg?label=release)](https://github.com/digimokan/ans-role-config-time/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Load Role Via `ansible-galaxy` Command](#load-role-via-ansible-galaxy-command)
* [Role Options](#role-options)
* [Contributing](#contributing)

## Purpose

* Set system [_hardware clock_](https://wiki.archlinux.org/index.php/System_time#Hardware_clock)
  to UTC.
* Optionally, enable continuous system time synchronization via
  [_systemd timesyncd_](https://wiki.archlinux.org/index.php/Systemd-timesyncd#Configuration)
  and [_systemd timedatectl_](https://wiki.archlinux.org/index.php/Systemd-timesyncd#Usage).
* Optionally, set local [time zone](https://wiki.archlinux.org/index.php/System_time#Time_zone).

## Supported Operating Systems

* Arch Linux.

## Quick Start

### Load Role Via `ansible-galaxy` Command

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans-role-config-time
     version: master
     name: config-time
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Configure system clock, time, and time zone"
         include_role:
           name: config-time
         vars:
           config_time_zone: "America/Vancouver"
   ```

## Role Options

See the role `defaults` file, for overridable vars:

  * [defaults/main.yml](../defaults/main.yml)

Define these _optional_ vars for the role:

  * `config_time_zone`: set the system time zone
    (see [tz database time zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
    for complete list)

    _NOTE: This var may be set to 'auto' instead of a time zone. The script will
           then call out to a geo-IP API to determine the time zone._

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans-role-config-time/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).


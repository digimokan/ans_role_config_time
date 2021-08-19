# ans_role_config_time

Ansible role to configure system clock, time, and time zone.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_time.svg?label=release)](https://github.com/digimokan/ans_role_config_time/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
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

* Arch Linux
* FreeBSD

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_time
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
         ansible.builtin.include_role:
           name: ans_role_config_time
         vars:
           time_zone_tz_name: "America/Vancouver"
   ```

## Role Options

See the role `defaults` file, for overridable vars:

  * [defaults/main.yml](../defaults/main.yml)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_time/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).


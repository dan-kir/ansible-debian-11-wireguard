ansible-debian-11-wireguard
==============================
[![Actively Maintained](https://img.shields.io/badge/Maintenance%20Level-Actively%20Maintained-green.svg)](https://gist.github.com/cheerfulstoic/d107229326a01ff0f333a1d3476e068d)

This role installs and configures a Wireguard peer with pre-generated keys.

Requirements
------------
Requires Ansible 2.10 or later. This role has only been tested on Debian 11 (Bullseye).

Wireguard keys need to be generated using `wg genkey` & `wg genpsk`.
These should then be pasted into `defaults/main.yml`

This role will not generate keys for you.

Role Variables
--------------
Wireguard keys, IP addresses and port defined in `defaults/main.yml`.

Dependencies
------------
None

Example Playbook
----------------

    - hosts: all
      become: yes
      become_method: sudo
      roles:
        - ansible-debian-11-hardening
        - ansible-debian-11-wireguard

Example Inventory
-----------------
*The `machine_hostname` variable is created for consistency when no DNS record exists*

*inventory.ini*

    [servers]
    192.168.0.11 ansible_ssh_user=admin machine_hostname=server01

*inventory.yml*

    ---
    all:
      hosts:
        192.168.0.11:
      vars:
        ansible_ssh_user: admin
        machine_hostname: server01

License
-------
GPL-3.0 License

Author Information
------------------
This role was created by Dan Kir

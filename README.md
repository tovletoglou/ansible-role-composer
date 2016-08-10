# Ansible Role: Composer on Centos 7

Installs Composer, the PHP Dependency Manager, on Centos 7, using `getcomposer.org/installer`

## Requirements

**PHP 5.4+** should be installed and working

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

The absolute path where Composer will be. Default `/usr/local/bin`.

    composer_directory: /usr/local/bin

If there is an update apply it (true | false).

    composer_keep_updated: true

This role will install the latest stable Composer version. If you want a fixed version define it here.

    composer_version: ''

Composer installation requires a temporary path to add the installer and build the actual composer. Define the path here.

    composer_installer_path: /usr/local/share/applications/composer

Checksum and hash algorithm for the installer.

    composer_installer_checksum: e115a8dc7871f15d853148a7fbac7da27d6c0030b848d9b3dc09e2a0388afed865e6a3d6b3c0fad45c48e2b5fc1196ae
    composer_installer_checksum_algorithm: sha384

Add the {{ composer_directory }} on system $PATH (true | false).
It will automatically check if the PATH exists, otherwise it will add it.

    composer_add_to_path: true

Remove Composer before the installation (true | false).
Warning: if you have Composer on a different path than
{{ composer_directory }} and {{ composer_installer_path }} it will not work.
Warning: use with caution!

    composer_remove: false

## Dependencies

No dependencies on ansible roles but you should have **PHP 5.4+** installed.

## Example Playbook

Installed with galaxy.ansible `ansible-galaxy install tovletoglou.composer`

    - hosts: all
      roles:
        - { role: tovletoglou.composer }

Installed as a playbook git submodule `git clone https://github.com/tovletoglou/ansible-role-composer.git playbook/roles/ansible-role-composer`

    ---

    - hosts: all
      roles:
        - { role: ansible-role-composer }

Sending custom vars

    - hosts: all
      roles:
        - { role: tovletoglou.composer }
      vars:
        composer_path: /usr/local/bin
        composer_keep_updated: false

After the playbook runs, `composer` will be placed in `/usr/local/bin/composer` (this location is configurable), and will be accessible via normal system accounts.

## License

MIT

## Author Information

Apostolos Tovletoglou [ansible-role-composer](https://github.com/tovletoglou/ansible-role-composer)

# Install podman on CentOS7 with minimal root

This git targets the best hosters I know: Uberspace ♥.

@luto tried to install podman and had some problems, so I share my existing scripts.

## Usage

### Using Ansible

Inside the ansible folder there are 4 .ansible playbooks.

- complete.ansible - this runs the other plays
- 01_immitate_uberspace.ansible - Installs some packages already present on uberspace
- 02_pre_setup.ansible - This is the part that needs root permissions (enable user namespaces and install container-selinux)
- 03_podman.ansible - This installs podman as a default user

All playbooks use the hostgroup ```podman```.

## Presetup

These playbooks should work on a clean CentOS7 install (Tested on CentOS Linux release 7.7.1908 (Core)) which is accessible for ansible.
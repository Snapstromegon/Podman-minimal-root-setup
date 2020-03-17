# Install podman on CentOS7 with minimal root

This git targets the best hosters I know: Uberspace ♥.

@luto tried to install podman and had some problems, so I share my existing scripts.

## Usage

### Using Ansible

Inside the ansible folder there are six .ansible playbooks.

- complete.ansible - this runs the other plays
- default_yum_install - this runs play 01 and 02, but installs podman via yum
- official_repo_rpms - this uses the official rpms, but installs them without yum
- 01_immitate_uberspace.ansible - Installs some packages already present on uberspace
- 02_pre_setup.ansible - This is the part that needs root permissions (enable user namespaces and install container-selinux)
- 03_podman.ansible - This installs podman as a default user

All playbooks use the hostgroup ```podman```.

## Presetup

These playbooks should work on a clean CentOS7 install (Tested on CentOS Linux release 7.7.1908 (Core)) which is accessible for ansible.

## Config

You need to adapt .config/containers/libpod.conf, since you need to set some paths if you're not using central paths for podman and its binarys (like runc). Those have to be absolut, so you need to include the username.

Replace all paths starting with ```/home/snapstromegon``` with ```/home/<your_username>```.
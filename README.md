# My Ubuntu Ansible Playbooks

This repository contains my highly opinionated and personalized Ansible playbooks for provisioning Ubuntu and Debian-based virtual machines, containers, and Raspberry Pi systems.

These playbooks automate DNS configuration, Docker installation, shell customization, CLI tool installation, and general system hardening that I commonly apply to new systems.

> **WARNING:** These playbooks are designed for my personal workflows and lab environments. Review every task before running them on any system you care about.

## Playbooks

### configure_dns.yml

Configures local DNS resolution using Stubby and DNS-over-TLS.

Features:

- Disables `systemd-resolved`
- Installs and configures Stubby
- Replaces `/etc/resolv.conf`
- Configures Cloudflare and Quad9 DNS-over-TLS upstream resolvers

### docker_install.yml

Installs and configures Docker.

Features:

- Removes legacy Docker packages
- Installs Docker Engine
- Installs Docker Compose plugin
- Enables Docker at boot
- Starts Docker services

### update_new.yml

Performs post-provisioning customization and quality-of-life improvements.

Note: The latest revision completely refactors `update_new.yml` to move large inline configuration blocks into Jinja2 templates and simplify provisioning logic for reliable, error-free execution across virtual machines and containers

Features:

- Ensures cloud-init startup ordering is respected
- Installs commonly used administration tools
- Installs Fastfetch from distro repositories when available
- Falls back to GitHub releases when Fastfetch is unavailable in repositories
- Configures needrestart for automatic service restarts
- Deploys customized .screenrc and .inputrc files
- Configures shell aliases and fzf integration
- Displays Fastfetch at login
- Configures journald retention limits
- Disables cloud-init after provisioning

Supported architectures:

- amd64 / x86_64
- arm64 / aarch64

Tested on:

- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Debian 13 (Trixie)
- Raspberry Pi OS (Debian-based)

## Usage

### Install Ansible

```bash
sudo apt update
sudo apt install -y ansible git
```

### Clone Repository

```bash
sudo mkdir -p /ansible_scripts
cd /ansible_scripts
sudo git clone https://github.com/networkabilityllc/MyUbuntuPlaybooks.git
```

### Run update_new.yml

```bash
cd /ansible_scripts/MyUbuntuPlaybooks
ansible-playbook update_new.yml --become
```

### Run configure_dns.yml

```bash
ansible-playbook configure_dns.yml --become
```

### Run docker_install.yml

```bash
ansible-playbook docker_install.yml --become
```

## License

This project is licensed under the MIT License. See the LICENSE file for details.

# My Ubuntu Ansible Playbooks

This repository contains my highly opinionated and personalized Ansible playbooks for setting up new Ubuntu VMs. These playbooks automate DNS setup, Docker installation, and system customization with additional tools and configurations.

> **:warning: WARNING: These playbooks are for reference only and should _not_ be used in a production environment under any circumstances. Use at your own risk!**

These work nicely for me, but review and adapt them carefully before use.

## Playbooks

1. **configure_dns.yml**  
    - Disables `systemd-resolved`  
    - Installs and configures Stubby as a DNS-over-TLS resolver  
    - Replaces `/etc/resolv.conf`  
    - Uses Cloudflare and Quad9 DNS providers  

2. **docker_install.yml**  
    - Removes legacy Docker versions  
    - Installs Docker and Docker Compose  
    - Ensures Docker is enabled and running at boot  

3. **update_new.yml**  
    - Ensures cloud-init service waits are respected by TTY  
    - Installs additional CLI tools (`neofetch`, `cowsay`, `fortune-mod`, `iftop`, `micro`, `duf`, etc.)  
    - Modifies `needrestart.conf` to auto-restart updated services  
    - Applies a custom `.screenrc` to root and all `/home` users  
    - Appends a personalized MOTD block to `.bashrc` with ASCII output  

## Usage

### Install Ansible

```bash
sudo apt install ansible -y
```

### Set Up Directories and Clone Repository

```bash
sudo mkdir /ansible_scripts
cd /ansible_scripts
sudo git clone https://github.com/networkabilityllc/MyUbuntuPlaybooks.git
```

### Run the Playbooks

```bash
cd /ansible_scripts/MyUbuntuPlaybooks
sudo ansible-playbook -i inventory update_new.yml
```

To run `configure_dns.yml`:
```bash
sudo ansible-playbook -i inventory configure_dns.yml
```

To run `docker_install.yml`:
```bash
sudo ansible-playbook -i inventory docker_install.yml
```

---

## Disclaimer

These playbooks are provided as-is, without any warranty. Use at your own risk. Review each task before running it on production systems.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

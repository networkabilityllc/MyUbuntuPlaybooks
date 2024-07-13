This repository contains Ansible playbooks for setting up new Ubuntu VMs. These playbooks automate the process of configuring DNS, installing Docker, and updating the system with additional tools and configurations.

/**
 * Playbooks
 *
 * This file contains the documentation for the playbooks used in the project.
 */
## Playbooks

1. **configure_dns.yml**: Configures DNS to use stubby with Cloudflare and Quad9 as the DNS over TLS providers.
    - Disables systemd-resolved
    - Installs and configures stubby
    - Replaces `/etc/resolv.conf` to use stubby for DNS resolution

2. **docker_install.yml**: Installs Docker and Docker Compose on the system.
    - Removes old versions of Docker
    - Installs Docker and Docker Compose
    - Ensures Docker service is running and enabled at boot

3. **update_new.yml**: Executes various system updates and configurations.
    - Ensures specific directories and configuration files exist
    - Modifies needrestart configuration
    - Configures screenrc settings
    - Installs additional applications (neofetch, cowsay, fortune-mod, iftop, net-tools)
    - Appends custom commands to `.bashrc` for root and users in `/home`

## Usage

To use these playbooks, follow the instructions below:

### Install Ansible

**First, install Ansible on your Ubuntu system:**
```
sudo apt install ansible -y 
```


### Set Up Directories and Clone Repository**

**Create the necessary directory and clone this repository:**

```
sudo mkdir /ansible_scripts
cd /ansible_scripts
sudo git clone https://github.com/networkabilityllc/MyUbuntuPlaybooks.git
```

### Run the Playbooks

**Navigate to the cloned repository and run the desired playbook. For example, to run configure_dns.yml:**

```
cd MyUbuntuPlaybooks
ansible-playbook -i localhost configure_dns.yml
```

### Disclaimer

These playbooks are provided as-is without any warranty. Use them at your own risk. Ensure you understand what each playbook does before running it on your system. The authors are not responsible for any damage or data loss that may occur from using these playbooks.
License

This project is licensed under the MIT License. See the LICENSE file for details.

MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

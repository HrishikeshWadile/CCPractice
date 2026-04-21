🎯 Aim

To write and execute an Ansible playbook for installing and starting NGINX on target machines.

⚙️ Requirements
Ansible installed on control machine (Ubuntu/Linux/WSL)
At least 1 target VM (Ubuntu preferred, e.g., Azure VM)
SSH access to target machine
📘 Theory

Ansible is a configuration management tool used to automate software installation and system configuration on multiple servers using YAML-based playbooks.

🖥️ Setup (Control Node → Target Node)
Example:
Control Machine → Your laptop / WSL
Target Machine → Azure VM (Ubuntu)

Test connection:

ssh azureuser@<target-ip>
📁 Inventory File (hosts.ini)
[webservers]
<target-ip> ansible_user=azureuser ansible_ssh_private_key_file=~/.ssh/id_rsa

Replace <target-ip> with your VM public IP

📜 Ansible Playbook (install_nginx.yml)
---
- name: Install and start NGINX on target server
  hosts: webservers
  become: yes

  tasks:
    - name: Update apt packages
      apt:
        update_cache: yes

    - name: Install NGINX
      apt:
        name: nginx
        state: present

    - name: Start NGINX service
      service:
        name: nginx
        state: started
        enabled: yes
🚀 Execution Steps
1. Check Ansible connection
ansible -i hosts.ini webservers -m ping

Expected output:

SUCCESS => pong
2. Run Playbook
ansible-playbook -i hosts.ini install_nginx.yml
3. Verify on browser

Open:

http://<target-ip>

You should see:

Welcome to NGINX
📌 Output
NGINX installed successfully
Service started automatically
Web server accessible via browser
🧾 Result

Ansible playbook successfully installed and configured NGINX on target server.

📘 Conclusion

Ansible automates software installation and configuration, making deployment faster and error-free across multiple servers.
# Flask Web App Deployment using Ansible

This project uses **Ansible** to automate the installation of Python, Flask, and deployment of a simple Flask web app on 3 remote servers.

---

## 🗂️ Project Structure
lask_ansible/
├── hosts # Ansible inventory file with target server details
├── flask_app/
│ └── app.py # Simple Flask web application
├── playbook.yml # Main Ansible playbook to install & run Flask app

# Ansible Overview

## 📌 What is Ansible?

Ansible is an open-source **automation tool** used for **configuration management**, **application deployment**, **orchestration**, and **task automation**. It allows you to automate IT infrastructure tasks such as provisioning servers, managing configurations, and deploying code with simple, human-readable YAML files called **Playbooks**.

It is **agentless**, meaning it doesn’t require any software or agent to be installed on the target nodes. It uses **SSH** to connect to remote machines by default.

---

## ✅ Why Use Ansible?

- **Simplicity and Ease of Use**  
  Ansible uses YAML syntax, which is straightforward and human-readable, even for those without deep programming knowledge.

- **Agentless Architecture**  
  No need to install agents on the managed nodes — reduces overhead and simplifies maintenance.

- **Idempotent Execution**  
  Ensures that running a playbook multiple times results in the same system state — no repeated changes.

- **Scalability**  
  Manage hundreds or thousands of servers from a single control machine.

- **Extensible and Powerful**  
  Supports roles, modules, templates, and plugins for organizing and extending functionality.

- **Community and Enterprise Support**  
  Backed by Red Hat with a strong community and Ansible Galaxy for reusable content.

---

## ⚙️ How Ansible Works

### Key Concepts:

- **Inventory**  
  A file (usually `hosts` or `inventory.ini`) that lists the target machines grouped by roles or environment.

- **Modules**  
  Reusable units of work (e.g., `apt`, `yum`, `copy`, `service`, `file`) that perform tasks on the remote hosts.

- **Playbooks**  
  YAML files that define a series of tasks to be executed on remote machines in a particular order.

- **Tasks**  
  Individual units of work defined in a playbook, using Ansible modules.

- **Roles**  
  A way to group related tasks, variables, templates, and files into reusable components.

- **Variables and Templates**  
  Dynamic content and configuration management using variables and Jinja2 templating.

### Execution Flow:

1. **Control Node** (your local machine or Ansible server) has:
   - Ansible installed
   - Inventory file
   - Playbooks

2. You run an Ansible command or playbook:
   ```bash
   ansible-playbook site.yml -i inventory.ini



🧰 Common Ansible Commands
Purpose	Command
Check Ansible version	ansible --version
Ping all hosts	ansible all -i inventory.ini -m ping
Run a command on all hosts	ansible all -i inventory.ini -a "uptime"
Install a package	ansible web -i inventory.ini -m apt -a "name=nginx state=present" -b
Copy file to remote	ansible all -i inventory.ini -m copy -a "src=file.txt dest=/tmp/"
Reboot servers	ansible all -i inventory.ini -m reboot -b
Run a playbook	ansible-playbook -i inventory.ini site.yml
Playbook with sudo (become)	ansible-playbook -i inventory.ini site.yml --become
Playbook with dry-run	ansible-playbook -i inventory.ini site.yml --check
Playbook with tag	ansible-playbook -i inventory.ini site.yml --tags "web"
List all hosts	ansible-inventory -i inventory.ini --list
List specific group hosts	ansible web -i inventory.ini --list-hosts
Check playbook syntax	ansible-playbook site.yml --syntax-check
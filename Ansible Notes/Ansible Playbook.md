#ansible 

An **Ansible Playbook** is a YAML-formatted file used to automate tasks and configurations across multiple servers or systems. It's the primary method to describe and execute automation tasks in Ansible.

- [[How important is the YAML indentation for Ansible Playbook]]
- [[Verifying Ansible Playbook]]
- [[Ansible Playbook Conditionals]]

### Key Components:

- **Hosts**: Define the target machines where tasks will run.
    
- **Tasks**: Specific actions to be performed on target machines.
    
- **Modules**: Pre-built Ansible tools (e.g., `yum`, `copy`, `service`) that perform tasks.
    
- **Roles**: Reusable groups of tasks, files, and configurations.
    
- **Variables**: Dynamic values or parameters within tasks or roles.
    

### Example of an Ansible Playbook:

```yaml
---
- name: Install and start Nginx web server
  hosts: webservers
  become: true

  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Ensure Nginx is running
      service:
        name: nginx
        state: started
        enabled: true
```

### Explanation:

- This playbook targets hosts listed in the group `webservers`.
    
- Uses `become: true` to run tasks with elevated privileges (sudo/root).
    
- Performs two tasks:
    
    1. Installs Nginx (`apt` module).
        
    2. Ensures Nginx service is running and set to start automatically (`service` module).
        

### Running a Playbook:

```bash
ansible-playbook my_playbook.yml -i inventory.ini
```

- `inventory.ini` defines hosts/groups to target.
    

Ansible Playbooks simplify managing complex automation by clearly defining actions, configurations, and environments in a single structured file.

![[Pasted image 20250417110452.png]]

![[Pasted image 20250417111048.png]]

![[Pasted image 20250417111114.png]]

![[Pasted image 20250417111136.png]]


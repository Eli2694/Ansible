#ansible 

## ansible.cfg

- **Purpose:** This is the core configuration file that customizes Ansible’s behavior.
    
- **Format:** It uses an INI-style format, with sections such as `[defaults]`, `[privilege_escalation]`, and others.
    
- **Settings:** In this file, you can define default inventory paths, connection settings (e.g., SSH parameters), module paths, timeout values, logging options, and more.
    
- **Location & Precedence:**
    
    - Ansible checks several locations in this order:
        
        - The file specified by the `ANSIBLE_CONFIG` environment variable.
            
        - `ansible.cfg` in the current working directory.
            
        - A file in the user’s home directory (e.g., `~/.ansible.cfg`).
            
        - The global configuration file (typically `/etc/ansible/ansible.cfg`).
            
    - Settings in a file higher on the list override those in lower-precedence files.

![[Pasted image 20250415162830.png]]

![[Pasted image 20250415162916.png]]


Understanding these files and how they interact is key to leveraging Ansible’s full power for automation, configuration management, and orchestration.
#ansible 


## 1. Conditionals Based on Facts:

Facts are automatically gathered system information about the managed host (such as OS, CPU, IP addresses, memory, etc.). You can access facts using `ansible_facts` to control conditional execution:

### Example:

```yaml
tasks:
  - name: "Install Apache on Ubuntu"
    apt:
      name: apache2
      state: present
    when: ansible_facts['os_family'] == "Debian"
```

- **Explanation**: The task runs **only if** the OS family is Debian (e.g., Ubuntu, Debian).
    

---

## 2. Conditionals Based on Variables:

You can use conditionals based on user-defined variables, inventory variables, or even dynamically registered variables.

### Example:

```yaml
vars:
  install_webserver: true

tasks:
  - name: "Install Webserver"
    yum:
      name: httpd
      state: present
    when: install_webserver | bool
```

- **Explanation**: This task runs only if the variable `install_webserver` is set to true.
    

### Example with registered variable:

```yaml
tasks:
  - name: Check if configuration file exists
    stat:
      path: /etc/httpd/conf/httpd.conf
    register: httpd_conf

  - name: Restart Apache if configuration file exists
    service:
      name: httpd
      state: restarted
    when: httpd_conf.stat.exists
```

- **Explanation**: `httpd_conf` holds results from the `stat` module, and the service restarts only if the file exists.
    

---

## 3. Re-using Conditionals (Task Includes):

If multiple tasks share the same conditional, you can avoid repetition by attaching a conditional to an entire group of tasks included from an external file or role.

### Example with `import_tasks`:

`main.yml`:

```yaml
tasks:
  - import_tasks: install-dependencies.yml
    when: ansible_facts['os_family'] == 'RedHat'
```

`install-dependencies.yml`:

```yaml
- name: Install common packages
  yum:
    name: "{{ item }}"
    state: present
  loop:
    - git
    - curl
    - wget
```

- **Explanation**: Every task in `install-dependencies.yml` executes **only if** the OS is part of the RedHat family.
    

### Example with role:

```yaml
tasks:
  - include_role:
      name: security-hardening
    when: security_hardening_enabled | default(false)
```

- **Explanation**: The entire role `security-hardening` executes conditionally based on the `security_hardening_enabled` variable.
    

---

## Key Points:

- **Facts**: Automatically gathered, ideal for conditional execution based on system states.
    
- **Variables**: User-defined, allowing dynamic control over task execution.
    
- **Re-use Conditionals**: Applying `when` statements to task files or roles prevents redundancy and simplifies readability.
    

This approach makes your playbooks concise, manageable, and adaptable.



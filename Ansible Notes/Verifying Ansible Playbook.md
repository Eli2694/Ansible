#ansible 

To verify and validate an **Ansible Playbook**, you can follow these practical steps:

---

## 1. **Syntax Check**

The simplest method to verify YAML syntax without running the playbook:

```bash
ansible-playbook --syntax-check playbook.yml
```

- This ensures your YAML syntax and indentation are correct.
    

---

## 2. **Dry Run (Check Mode)**

This mode simulates the execution of your playbook without applying any changes:

```bash
ansible-playbook playbook.yml --check
```

- It helps verify tasks and identifies potential errors or unexpected behavior.
    

---

## 3. **Verbose Output**

Increase verbosity to understand each step Ansible performs during execution:

```bash
ansible-playbook playbook.yml -v
```

- Use multiple `v` flags for greater detail:  
    `-vv`, `-vvv`, `-vvvv`
    

---

## 4. **List Tasks**

Display a list of tasks in your playbook without executing them:

```bash
ansible-playbook playbook.yml --list-tasks
```

- This verifies that Ansible recognizes your defined tasks.
    

---

## 5. **List Hosts**

Verify which hosts your playbook will run against:

```bash
ansible-playbook playbook.yml --list-hosts
```

- This ensures correct targeting of your inventory.
    

---

## 6. **Linting (ansible-lint)**

Use a linting tool to detect best practice issues and potential errors:

```bash
ansible-lint playbook.yml
```

- You can install it via pip if needed:
    
    ```bash
    pip install ansible-lint
    ```

![[Pasted image 20250417113222.png]]


---

## Recommended Workflow:

1. **Syntax Check:** Quickly catch YAML mistakes.
    
2. **Dry Run:** See what would change.
    
3. **Verbose Output:** Troubleshoot detailed issues.
    
4. **Linting:** Improve quality and maintainability.
    

---

- [[Ansible Playbook --diff mode]]

**Ansible Diff Mode** (`--diff`) shows you the exact changes Ansible would apply to configuration files during execution. It highlights differences between the current and proposed states clearly and concisely.

### Why Use Diff Mode?

- Clearly identify changes before applying them.
    
- Safely audit playbook impact.
    
- Helps troubleshooting by showing exact file modifications.
    

### How to Run Diff Mode

Combine `--diff` with `--check` (dry run):

```bash
ansible-playbook playbook.yml --check --diff
```

Or run normally (changes will apply) with diff:

```bash
ansible-playbook playbook.yml --diff
```

### Example Output

```diff
TASK [Update configuration file] ******************************************
--- before: /etc/nginx/nginx.conf
+++ after: /tmp/ansible-tmp-1713337707.34-4623413834567/nginx.conf.j2
@@ -1,4 +1,4 @@
 user nginx;
-worker_processes auto;
+worker_processes 4;
 error_log /var/log/nginx/error.log warn;
 pid /var/run/nginx.pid;
```

- Lines beginning with `-` will be removed.
    
- Lines beginning with `+` will be added.
    
### Limitations and Notes:

- Works best with modules that manage files or configuration (`template`, `copy`, `lineinfile`, etc.).
    
- Does **not** show diffs for binary files or non-file operations (like service restarts, package installations, etc.).
    

### Recommended Usage:

- Always run a diff check (`--check --diff`) before applying major changes in production environments.
    
- Incorporate it into your Ansible playbook review process for safer deployments.
    

In short, the `--diff` option in Ansible playbooks is extremely useful for safely verifying configuration changes and maintaining transparency in automation.
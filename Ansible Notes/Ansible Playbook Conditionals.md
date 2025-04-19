#ansible 

- [[Ansible Conditionals based on facts, variables, re-use]]

## 1. The `when` keyword

At its simplest, you tack a `when:` onto any task (or block, role‑include, etc.):

```yaml
- name: Install httpd on Red Hat family
  yum:
    name: httpd
    state: present
  when: ansible_facts['os_family'] == 'RedHat'
```

- **Expression**: any Jinja2 boolean expression
    
- **Facts & variables**: you can reference facts (`ansible_facts`), inventory vars, group vars, registered results, etc.
    
- **Strings, numbers, lists**: you can compare (`==`, `!=`, `>`, `<`, `in`, `not in`)
    

## 2. Combining multiple conditions

Use standard Python boolean operators:

```yaml
when:
  - ansible_facts['os_family'] == 'Debian'
  - ansible_facts['distribution_major_version'] | int >= 10
```

You can also write it inline with `and`/`or`:

```yaml
when: ansible_facts['os_family'] == 'Debian' and (myvar is defined)
```

## 3. Checking variable existence

- `is defined` / `is undefined`
    
- `variable | default('')`
    

```yaml
when: my_optional_var is defined and my_optional_var != ''
```

## 4. Negating a condition

Use `not`:

```yaml
when: not ansible_facts['virtualization_role'] == 'guest'
```

## 5. Conditional result evaluation

Sometimes you want Ansible to mark a task as failed or changed based on its own output, not just run/skipped:

```yaml
- name: Run custom check
  command: /usr/local/bin/check_something
  register: check
  failed_when: "'ERROR' in check.stdout"
  changed_when: check.rc == 0 and "'OK' in check.stdout"
```

- **`failed_when:`** mark failure if true
    
- **`changed_when:`** override changed status
    

## 6. Using `when` with loops

Apply the condition to each item in the loop:

```yaml
- name: Create only non‑root users
  user:
    name: "{{ item }}"
  loop: "{{ user_list }}"
  when: item != 'root'
```

## 7. `block`‑level conditionals

Group tasks and apply one `when:`:

```yaml
- block:
    - name: Start service
      service: name=myapp state=started
    - name: Wait for port
      wait_for: port=8080
  when: deploy_env == 'production'
```

## 8. Best practices

- **Keep expressions simple.** If they get long, register to a variable first or split into multiple tasks.
    
- **Use facts** (`ansible_facts`) or inventory vars rather than shelling out to check state.
    
- **Test early**: add a `debug: var=…` to verify your conditional’s logic.
    

With these tools you can make your playbooks smart—only running what you need, when you need it.

## More Examples

![[Pasted image 20250417124345.png]]

![[Pasted image 20250417124404.png]]
![[Pasted image 20250417124451.png]]

![[Pasted image 20250417124508.png]]

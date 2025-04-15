#ansible

Ansible is an open-source automation engine that simplifies complex IT tasks like configuration management, application deployment, and task automation. It uses a simple, human-readable language1 (YAML) in "playbooks" to define automation jobs.

**Key Concepts:**

- **Agentless:** It connects to managed nodes via SSH and doesn't require any agent software installation.
- **Inventory:** A file (or dynamic source) that lists the managed hosts and groups them.
- **Modules:** Units of code that Ansible executes on managed nodes to perform tasks.
- **Tasks:** Actions that call Ansible modules with specific parameters.
- **Playbooks:** Ordered lists of tasks that define the desired state or automation workflow.
- **Roles:** Reusable and organized units of Ansible content (tasks, handlers, variables, etc.).
- **Idempotent:** Running the same playbook multiple times results in the same system state.

In essence, Ansible allows you to automate repetitive and complex IT operations efficiently and consistently across your infrastructure. It have a **Large Community and Extensive Documentation:** Provides ample resources and support.

- [[Ansible Config File (ansible.cfg)]]
- [[YAML File]]

# Role

In Ansible, you might write 100–200 lines of configuration code (or even more). To keep things organized and maintainable, you can use **roles**. Roles let you structure your tasks, handlers, variables, and more into separate folders, making it easier to understand and reuse your automation code.

---

## Creating a Role

Use the following command to create a new Ansible role:

```bash
ansible-galaxy init <role_name>
```

```mermaid
    graph TD;
    A[Ansible Role]
    A --> B[defaults]
    A --> C[files]
    A --> D[handlers]
    A --> E[meta]
    A --> F[README.md]
    A --> G[tasks]
    A --> H[templates]
    A --> I[tests]
    A --> J[vars]

### task : 
    In they task directory contain list of action we wnats to exqute

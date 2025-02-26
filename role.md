# role:
    In ansible we will write a more they 100 -200 lines of code to organise those lines by using they roles to understand they code easier 

## To create they role by using 
    
    ```
    ansible-galaxy init <filename>
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

### asible collection:

Ansible Galaxy Collections provide a standardized way to package, distribute, and reuse Ansible content

for example to download they aws package:

We wants to dowload they aws colection to use

1. we want to install boto3
     we wnat to create they environment 
        1. python3 -m venu myenu
        2. source myenv/bin/activate
2.  ```

    ansible-galaxy collection install <path>
    ```
   
    if we want to install they latest version  then :
        ```
        ansible-galaxy collection install <path> atlast --force
***boto3*** is they python module to acess they api

3. ***Task***  (create they ec2 instance by using they ansible-playbook):

        To create they ec2 instance we need they 
                
                1. access key 
                2. secret key
        To secure they key we use they ***vault***

## Setup Vault 

1. Create a password for vault

```
openssl rand -base64 2048 > vault.pass
```

2. Add your AWS credentials using the below vault command

```
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```

3. Inside they yaml file we will place the key

4. we will be pass they key : {{}}
 ### for example :
 
            aws_access_key: "{{ec2_access_key}}"
            aws_secret_key: "{{ec2_secret_key}}" 
   
    Inside they jaml file we want to save they keys by
             
             ec2_access_key: xxxxxxxxxxx
             ec2_secret_key: zzzzzzzzzzzzz

5. To execute : 
    ``` 
        ansible-playboook -i inventory.ini <name of they json file> --vault-password-file <name of they password generated file>

| Feature         | Built-in Git Code (Internals) | Git Collections (External Libraries) |
|---------------|----------------------|-------------------------|
| **Installation** | Comes with Git source code | Needs to be installed separately |
| **Maintenance** | Managed by Git Core Team | Maintained by third-party developers |
| **Scope** | Core Git functionalities in C | Integrations for other languages |
| **Examples** | `git_commit_create()`, `git_clone()` (in C) | `GitPython`, `JGit`, `NodeGit` |

In they inventory file we use to group they users:
            group_vars/all/<group_name>.yaml
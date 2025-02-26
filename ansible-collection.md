# Ansible Collection Setup

This repository contains instructions for setting up and using Ansible collections, specifically for AWS automation.

## **1. Install boto3 and Create a Virtual Environment**

Before using the AWS collection, install `boto3`, the Python module for accessing AWS APIs.

### **Setup Virtual Environment**
```sh
python3 -m venv myenv
source myenv/bin/activate
pip install boto3
```

## **2. Install the AWS Collection**

To install the AWS collection using `ansible-galaxy`:
```sh
ansible-galaxy collection install amazon.aws
```

To install the latest version and overwrite an existing installation:
```sh
ansible-galaxy collection install amazon.aws --force
```

## **3. Task: Create an EC2 Instance using Ansible Playbook**

### **Required AWS Credentials:**
- **AWS Access Key**
- **AWS Secret Key**

To secure the keys, use **Ansible Vault**.

## **4. Setup Ansible Vault**

### **Create a password file for Vault:**
```sh
openssl rand -base64 32 > vault.pass
```

### **Add AWS credentials to the Vault:**
```sh
ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
```

### **Inside `group_vars/all/pass.yml`, store the AWS keys securely:**
```yaml
ec2_access_key: xxxxxxxxxxx
ec2_secret_key: zzzzzzzzzzzzz
```

### **Reference the keys in your playbook:**
```yaml
aws_access_key: "{{ ec2_access_key }}"
aws_secret_key: "{{ ec2_secret_key }}"
```

### **Execute the playbook:**
```sh
ansible-playbook -i inventory.ini <playbook_name>.yml --vault-password-file vault.pass
```

## **5. Difference Between Built-in and Collection Modules**

| Feature           | Built-in Ansible Modules         | Ansible Collections          |
|------------------|--------------------------------|-----------------------------|
| **Installation** | Comes pre-installed with Ansible | Needs to be installed separately |
| **Maintenance**  | Managed by Ansible Core Team   | Maintained by Red Hat, vendors, or the community |
| **Scope**       | Basic automation (files, services, users) | Advanced automation (cloud, networking, security) |
| **Examples**    | `copy`, `file`, `debug`, `service` | `amazon.aws.ec2_instance`, `kubernetes.core` |

## **6. Inventory File Usage**

In the inventory file, we use groups to manage different servers and users.
```yaml
group_vars/all/<group_name>.yaml
```
### Error Handling in Ansible:
Error handling in Ansible is the process of managing failures that occur during playbook execution to prevent disruptions and ensure smooth automation.

## Why is Error Handling Important?

1. Prevents playbooks from stopping unexpectedly.
2. Helps in debugging and logging failures.
3. Ensures automation tasks are more reliable.

## 1️⃣ Ignore Errors (ignore_errors)

Allows the playbook to continue execution even if a task fails.

### 🔹 Example:
```
- name: Install a package
  ansible.builtin.yum:
    name: nginx
    state: present
  ignore_errors: yes
```
### ✅ Use Case → When a failure is not critical, and the playbook should continue.

## 2️⃣ Fail Fast (failed_when):

 Custom conditions to determine when a task should be marked as failed.
🔹 Example: Fails only if the return code is not 0 or 1
### 🔹 Example:


```
- name: Check disk space
  shell: df -h / | awk 'NR==2 {print $5}' | sed 's/%//'
  register: disk_usage
  failed_when: disk_usage.stdout | int > 90
```
### ✅ Use Case → When you want more control over what is considered a failure.

### 3️⃣ Force Failure (fail Module)

### 🔹 Example:

Explicitly fails a playbook with a custom error message.
🔹 Example:
```
- name: Stop playbook if a condition is met
  ansible.builtin.fail:
    msg: "Insufficient disk space. Aborting!"
  when: disk_usage.stdout | int > 95
```
### ✅ Use Case → When a certain condition must cause failure to stop further execution.
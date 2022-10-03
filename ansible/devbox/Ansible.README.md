### **Ansible Playbook for DevBox Configuration**

These are instructions for leveraging the Ansible Playbook that will configure an EC2 DevBox for building Okera source.

#### **Prerequisites**

**Ansible**

To run this playbook, you will need to have Ansible. Details are at [https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html). In it's simplest form, installation should happen thusly:

```shell
brew install ansible
```

**Access**

This playbook assumes you have already gained access to the following systems in their prescribed ways.

* **GitHub:** ssh key stored at `~/.ssh/id_rsa` and `~/.ssh/id_rsa.pub`
* **Gerrit:** ssh key the same as GitHub
* **AWS:** Credentials file and config file already present on your local machine

#### **Setting up the Playbook**

There are two files you will need to provide input into:

**Host(s)**

* **File:** [inventory/hosts.yml](inventory/hosts.yml)
* **Content:** Add your hosts to this file just after the "hosts" line, one host IP address per line.

**Variables**

* **File:** [inventory/group_vars/all.yml](inventory/group_vars/all.yml)
* **Content:** Update each of the entries in this file to match your own credentials and local file names for each variable.

#### Running the Playbook

From within the [ansible/devbox](../../ansible/devbox) directory, execute the following command:

```shell
ansible-playbook -i inventory site.yml
```
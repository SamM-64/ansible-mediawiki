# Ansible-Mediawiki

# How To use Ansible

Based on the infrastructure in the network folder.

## Create virtualenv

```bash
# To create
virtualenv -p python3 <nom_de_mon_virtual_env>
# To activate
source <nom_de_mon_virtual_env>/bin/activate
# To deactivate
deactivate
```
### Install Ansible

```bash
pip install ansible
```

### Create a playbook

```bash
mkdir ansible
cd ansible
touch install-apache.yml && touch install-mariadb.yml && touch install-mediawiki.yml
```

### Create a inventory file

```bash
touch inventory.ini
```

### Create a role

```bash
ansible-galaxy init <nom_de_mon_role>
```

### Run playbook

```bash
ansible-playbook -i inventory.ini install-apache.yml
ansible-playbook -i inventory.ini install-mariadb.yml
ansible-playbook -i inventory.ini install-mediawiki.yml --ask-vault-pass
```

### ping all hosts

```bash
ansible all -m ping -i inventory.ini
```

### allow media wiki

```sql
GRANT ALL PRIVILEGES ON *.mediawiki TO 'mediawiki'@'%' IDENTIFIED BY 'mediaDBpassw0rd' WITH GRANT OPTION;
```
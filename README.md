# Ansible-Mediawiki

# Comment utiliser Ansible

Basé sur l'infrastructure du dossier network.

## Créer un environnement virtuel

```bash
# # Pour créer
virtualenv -p python3 <nom_de_mon_virtual_env>
# Pour activer
source <nom_de_mon_virtual_env>/bin/activate
# Pour désactiver
deactivate
```
### Installer Ansible

```bash
pip install ansible
```

### Créer un playbook

```bash
mkdir ansible
cd ansible
touch install-apache.yml && touch install-mariadb.yml && touch install-mediawiki.yml
```

### Créer un fichier d'inventaire

```bash
touch inventory.ini
```

### Créer un rôle

```bash
ansible-galaxy init <nom_de_mon_role>
```

### Exécuter le playbook

```bash
ansible-playbook -i inventory.ini install-apache.yml
ansible-playbook -i inventory.ini install-mariadb.yml
ansible-playbook -i inventory.ini install-mediawiki.yml --ask-vault-pass
```

### Vérifier la connectivité avec tous les hôtes

```bash
ansible all -m ping -i inventory.ini
```

### Autoriser MediaWiki

```sql
GRANT ALL PRIVILEGES ON *.mediawiki TO 'mediawiki'@'%' IDENTIFIED BY 'mediaDBpassw0rd' WITH GRANT OPTION;
```
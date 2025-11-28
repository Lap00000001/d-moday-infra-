If all going fine, this should make really fast and easy the creation of a network, with a database, a serveur file, a DC1, a PFsense, a Wazuh/zabbix, an ansible and other little things, all already configured

1th mission will be to configure the correct Ip in the inventory/hosts.ini

2th mission will be to adapted the inventory/group_vars/all.yml
METTON_BUCKET and the secret keys

3th mission will be to adapted the 

Test each rules before deployement : wazuh-logtest (command to use on manager) in order to check it. (tips : play this commande on a test VM)

Utilise ansible-vault pour : mots de passe restic, clefs S3, clefs SSH d’accès vers cibles.
Pas de secrets en clair dans le repo.
Limite les accès SSH et utilise des clés dédiées deploy_key pour GitHub/Ansible.

Chiffrer vault/credentials.yml via ansible-vault create vault/credentials.yml.

Lancer en mode dry-run :
ansible-playbook -i inventory/hosts.ini playbooks/backup.yml --check --diff --ask-vault-pass

Lancer sur une cible test :
ansible-playbook -i inventory/hosts.ini playbooks/backup.yml --ask-vault-pass

Vérifier logs restic : /var/log/restic-<host>.log et restic snapshots.

Pour Wazuh : déployer sur une VM test, vérifier /var/ossec/logs/ossec.log, tester règle avec wazuh-logtest.

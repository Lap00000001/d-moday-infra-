If all going fine, this should make really fast and easy the creation of a network, with a database, a serveur file, a DC1, a PFsense, a Wazuh/zabbix, an ansible and other little things, all already configured

1th mission will be to configure the correct Ip in the inventory/hosts.ini

2th mission will be to adapted the inventory/group_vars/all.yml

3th mission will be to adapted the 

Test each rules before deployement : wazuh-logtest (command to use on manager) in order to check it. (tips : play this commande on a test VM)

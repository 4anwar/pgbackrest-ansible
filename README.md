# pgbackrest-ansible
Ansible playbooks to install and configure pgbackret Server and DB Servers.

1. git pull repo
2. build pgbackrest binaries for ubuntu version and copy to binaries directory
3.
```bash 
├── binary
│   ├── pgbackrest-2.34-16.04
│   └── pgbackrest-2.34-18.04
├── inventory
├── pgbackrest-client
│   ├── configure-dbserver.yml
│   ├── pgisntall.yml
│   └── vars
│       ├── prod.yml
│       ├── stage.yml
│       └── uat.yml
├── pgbackrest-repository
│   ├── configure-server.yml
├── public_keys
└── README.md
```
4. Add ansible modules used by the playbooks

   `ansible-galaxy collection install community.postgresql`

   `ansible-galaxy collection install community.general`

   `ansible-galaxy collection install ansible.posix`
   

5. #Create ansible user with right key in authorized_keys

6. #Change env variables in inventory and yml files

7. #Run playbook to setup pgbackrest repository server after updating the vars

   `ansible-playbook -i inventory pgbackrest-repository/configure-server.yml  --check`

8. #Run playbook to setup postgres db server for pgbackrest backup after updating the vars

   `ansible-playbook -i inventory pgbackrest-client/configure-dbserver.yml  --check`

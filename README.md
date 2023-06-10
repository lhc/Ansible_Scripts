# Ansible Playbooks #

This repository contain all the playbooks to deploy LHC infrastructure

#
## How to Set up the enviroment for all playbook ##

Create a python enviroment and install the required packages ###

```
python3.10 -m venv ansible_env 
```

After creating the enviroment activate it.

```
source ansible_env/bin/activate
```

after the enviroment is activated install all packages required

```
pip install -r requirements.txt
```

# Deployment

Activate the ansible enviroment and run

```
ansible-playbook chirpstack/deploy.yml
```


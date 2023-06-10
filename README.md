# Chirpstack development #

This repository contain a recipe to deploy a chirpstack using Docker-Compose. This recipe by default will configure the gateway-bridge with AU915 fot other frequencies change files.

**Important** - This deployment is for developing purpose and do not have any security feature, please follow the recomendation at the official repository.

Any question please look for the oficial documentation [Chirpstack](https://www.chirpstack.io/)

#
## How to Set up the enviroment ##

Create a python enviroment and install the required packages ###

```
python3.10 -m venv chirpstack_env
```

After creating the enviroment activate it.

```
source chirpstack_env/bin/activate
```

after the enviroment is activated install all packages required

```
pip install -r requirements.txt
```

# Deployment

Activate the ansible enviroment and run

```
ansible-playbook deploy.yml
```

After completing running the recipe access the server with port 8080
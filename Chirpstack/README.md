# Ansible Playbooks #

This repository contain a recipe to deploy a chirpstack using Docker-Compose. This recipe by default will configure the gateway-bridge with AU915 fot other frequencies change files.

**Important** - This deployment is for developing purpose and do not have any security feature, please follow the recomendation at the official repository.

Any question please look for the oficial documentation [Chirpstack](https://www.chirpstack.io/)

# Deployment

Activate the ansible enviroment and run

```
ansible-playbook deploy.yml
```

After completing running the recipe access the server with port 8080
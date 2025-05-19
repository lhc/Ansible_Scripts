# Raspberry Pi LoRaWAN Gateway

This directory contains Ansible playbooks and configurations for deploying and managing Raspberry Pi LoRaWAN gateways.

## Overview

The Raspberry Pi LoRaWAN gateway setup includes:
- Semtech Packet Forwarder
- Gateway Bridge
- MQTT client for Chirpstack integration
- System configuration and monitoring

## Prerequisites

- Raspberry Pi (3B+ or 4 recommended)
- LoRa concentrator (Raspberry Pi LoRa HAT)
- Ansible 2.9 or higher
- Python 3.6 or higher
- SSH access to the Raspberry Pi

## Configuration

1. Configure inventory:
   - Copy `inventory/hosts.example` to `inventory/hosts`
   - Update the inventory file with your Raspberry Pi details

2. Configure gateway settings:
   - Copy `vars/gateway.example.yml` to `vars/gateway.yml`
   - Update the gateway configuration with your settings:
     - Gateway ID
     - Server address
     - Frequency plan
     - Other specific settings

## Deployment

```bash
# Make sure your virtual environment is activated
source ../chirpstack_env/bin/activate  # Linux/macOS
..\chirpstack_env\Scripts\activate    # Windows

# Run the playbook
ansible-playbook -i inventory deploy.yml
```


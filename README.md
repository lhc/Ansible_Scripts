# LHC Ansible Project

This project contains Ansible playbooks and configurations for deploying and managing LoRaWAN infrastructure components, including Chirpstack, RabbitMQ, and Raspberry Pi LoRaWAN gateways.

## Project Structure

```
.
├── Chirpstack/              # Chirpstack deployment and configuration
│   ├── inventory/          # Ansible inventory files
│   ├── roles/             # Ansible roles for different components
│   │   ├── chirpstack/    # Chirpstack server role
│   │   ├── mosquitto/     # MQTT broker role
│   │   ├── postgres/      # PostgreSQL database role
│   │   ├── rabbitmq/      # RabbitMQ role
│   │   └── redis/         # Redis role
│   └── deploy.yml         # Main deployment playbook
├── RPI_LoRawan/           # Raspberry Pi LoRaWAN gateway configurations
└── requirements.txt       # Python dependencies
```

## Components Overview

- **Chirpstack**: LoRaWAN Network Server
  - [Detailed Documentation](Chirpstack/README.md)
  - Handles device management and message routing
  - Integrates with RabbitMQ for event handling

- **Raspberry Pi LoRaWAN Gateway**
  - [Detailed Documentation](RPI_LoRawan/README.md)
  - Gateway configuration and management
  - Integration with Chirpstack

## Prerequisites

- Ansible 2.9 or higher
- Python 3.6 or higher
- Docker and Docker Compose
- SSH access to target servers

## Install
```
    apt install python3.12-venv
```

## Environment Setup

1. Clone the repository:
```bash
git clone <repository-url>
cd LHC_Ansible
```

2. Set up Python virtual environment:
```bash
# Create a new virtual environment
python3 -m venv chirpstack_env

# Activate the virtual environment
# On Linux/macOS:
source chirpstack_env/bin/activate
# On Windows:
.\chirpstack_env\Scripts\activate

# Verify Python version
python --version

# Upgrade pip
pip install --upgrade pip
```

3. Install Python dependencies:
```bash
# Make sure your virtual environment is activated
pip install -r requirements.txt
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request


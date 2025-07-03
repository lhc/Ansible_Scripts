# Chirpstack Deployment

This directory contains Ansible playbooks and configurations for deploying a complete Chirpstack LoRaWAN Network Server stack.

## Components

### Chirpstack Server
- LoRaWAN Network Server
- Handles device management, uplink/downlink messages
- Integrates with RabbitMQ for event handling
- Uses PostgreSQL for data storage
- Uses Redis for caching

### RabbitMQ
- Message broker for Chirpstack integrations
- Handles device events and commands
- Uses MQTT plugin for MQTT protocol support
- Configured with dedicated vhost for Chirpstack

### Mosquitto
- MQTT broker for gateway backend
- Handles gateway events and commands
- Uses standard MQTT port (1883)

### PostgreSQL
- Database for Chirpstack
- Stores device data, applications, and configurations

### Redis
- Caching layer for Chirpstack
- Improves performance for frequently accessed data

## Prerequisites
- Ansible 2.9 or higher
- Python 3.6 or higher
- Docker and Docker Compose
- SSH access to target servers

## Grafana

## Node-Red


## Deployment

## prerequisite client running ansible 
```
apt install pkcs11_provider
apt install sshpass
```

```bash
# Make sure your virtual environment is activated
source chirpstack_env/bin/activate  # Linux/macOS
..\chirpstack_env\Scripts\activate    # Windows

# Run the playbook
ansible-playbook -i inventory deploy.yml --ask-pass --ask-become-pass
```

This will deploy:
- Chirpstack server
- RabbitMQ with MQTT plugin
- Mosquitto MQTT broker
- PostgreSQL database
- Redis cache

### Chirpstack
- Web interface: `http://<server-ip>:8080`
- Default credentials: admin/admin

### RabbitMQ
- Management interface: `http://<server-ip>:15672`
- Default credentials: defined in screts.yml

### Node-Red
- Port : 1880

### Grafana
- Port: 3000

## Troubleshooting

### Common Issues

1. RabbitMQ Connection Issues
   - Check if the vhost `/chirpstack` exists
   - Verify user permissions
   - Check RabbitMQ logs: `docker logs chirpstack_rabbitmq_1`

2. Chirpstack Integration Issues
   - Verify MQTT integration is enabled
   - Check environment variables
   - Check Chirpstack logs: `docker logs chirpstack_chirpstack_1`

3. Gateway Connection Issues
   - Verify Mosquitto is running
   - Check gateway configuration
   - Check Mosquitto logs: `docker logs chirpstack_mosquitto_1`

4. Database Issues
   - Check PostgreSQL logs: `docker logs chirpstack_postgres_1`
   - Verify database migrations: `docker exec chirpstack_chirpstack_1 chirpstack migrate`

5. Redis Issues
   - Check Redis logs: `docker logs chirpstack_redis_1`
   - Verify Redis connection: `docker exec chirpstack_redis_1 redis-cli ping`

## Component Interactions

1. Gateway to Chirpstack:
   - Gateways connect to Mosquitto (port 1883)
   - Events are forwarded to Chirpstack

2. Chirpstack to RabbitMQ:
   - Chirpstack connects to RabbitMQ (port 8883)
   - Device events are published to RabbitMQ
   - Commands are received from RabbitMQ

3. Chirpstack to Database:
   - PostgreSQL stores persistent data
   - Redis caches frequently accessed data

## Maintenance

### Backup
- Database backup: `docker exec chirpstack_postgres_1 pg_dump -U chirpstack chirpstack > backup.sql`
- Configuration backup: Copy the `configuration` directory

### Updates
1. Pull latest changes
2. Update configuration if needed
3. Run the playbook again

### Logs
- All logs are available through Docker:
  ```bash
  docker logs chirpstack_chirpstack_1
  docker logs chirpstack_rabbitmq_1
  docker logs chirpstack_mosquitto_1
  docker logs chirpstack_postgres_1
  docker logs chirpstack_redis_1
  ```

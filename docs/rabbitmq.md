# RabbitMQ

## Basic Commands
Start RabbitMQ Node:
```bash
sudo rabbitmqctl start_app
```
Stop RabbitMQ Node:
```bash
sudo rabbitmqctl stop_app
```
Change the log level to INFO,...,DEBUG:
```bash
sudo rabbitmqctl <-n rabbit@target-host> set_log_level debug
```
## Cluster 
Get Cluster Status
```bash
sudo rabbitmqctl cluster_status
```
Join the cluster (from the joining node):
```bash
sudo rabbitmqctl join_cluster <RABBIT@HOSTNAME>
```
## Quorum Queues

A Script to grow the quorum queues to all available RabbitMQ nodes in Cluster:
```bash
#!/bin/bash

# Define Queue Pattern
QUEUE_PATTERN=".*"

# Get list of all cluster nodes (disc + ram nodes)
RAW_NODES=$(sudo rabbitmqctl cluster_status --formatter=json | jq -r '.disk_nodes[]?, .ram_nodes[]?')

# Populate the TARGET_NODES array
TARGET_NODES=()
for node in $RAW_NODES; do
  TARGET_NODES+=("$node")
done

# Debug: Print for verification
echo "🐇 Detected cluster nodes:"
for node in "${TARGET_NODES[@]}"; do
  echo "  - $node"
done

# Get all vhosts
VHOSTS=$(sudo rabbitmqctl list_vhosts -q)

for vhost in $VHOSTS; do
  echo "📁 Processing vhost: $vhost"
  for node in "${TARGET_NODES[@]}"; do
    echo "🔁 Growing queues on node: $node"
    sudo rabbitmq-queues grow "$node" "all" \
      --vhost-pattern "$vhost" \
      --queue-pattern "$QUEUE_PATTERN"
  done
done
```
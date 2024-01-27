# Docker Compose for YugabyteDB Cluster

This Docker Compose configuration sets up a three-node YugabyteDB cluster for testing purposes. The configuration includes dependencies between nodes to ensure proper initialization order.

## How to Use

1. **Create a custom network:**
    ```bash
    docker network create custom-network
    ```

2. **Start the YugabyteDB cluster:**
    ```bash
    docker-compose up -d
    ```

3. **Access YugabyteDB services:**
    - Node 1: [http://localhost:7001](http://localhost:7001)
    - Node 2: [http://localhost:7002](http://localhost:7002)
    - Node 3: [http://localhost:7003](http://localhost:7003)

## Services

### yugabytedb-node1

- Image: yugabytedb/yugabyte:latest
- Ports: 15433:15433, 7001:7000, 9001:9000, 5433:5433
- Volume: ~/yugabyte_volume/node1:/home/yugabyte/yb_data

### yugabytedb-node2

- Image: yugabytedb/yugabyte:latest
- Ports: 15434:15433, 7002:7000, 9002:9000, 5434:5433
- Volume: ~/yugabyte_volume/node2:/home/yugabyte/yb_data
- Depends on: yugabytedb-node1

### yugabytedb-node3

- Image: yugabytedb/yugabyte:latest
- Ports: 15435:15433, 7003:7000, 9003:9000, 5435:5433
- Volume: ~/yugabyte_volume/node3:/home/yugabyte/yb_data
- Depends on: yugabytedb-node1, yugabytedb-node2

## Troubleshooting

- If you encounter issues, check the logs of each node for more details:
    ```bash
    docker logs yugabytedb-node1
    docker logs yugabytedb-node2
    docker logs yugabytedb-node3
    ```

- Ensure that there are no firewall rules or network issues preventing communication between the nodes.

## Disclaimer

This Docker Compose setup is designed for testing purposes and may not be suitable for production environments. Use it in a controlled environment and make adjustments as needed.

Feel free to explore and modify the configuration based on your requirements.

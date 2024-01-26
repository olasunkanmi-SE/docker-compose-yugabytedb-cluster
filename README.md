# docker-compose-yugabytedb-cluster

This Docker Compose configuration sets up a three-node YugabyteDB cluster, providing a distributed, fault-tolerant database system

# Three-Node YugabyteDB Cluster with Docker

**Description:**
Each node is encapsulated within its own Docker container, facilitating easy deployment and testing.

**Key Features:**

- **YugabyteDB Version:** The latest version of YugabyteDB is utilized for each node, ensuring access to the latest features and improvements.
- **Custom Network:** The nodes are connected to a custom Docker network (`custom-network`), enabling secure communication between the containers.
- **Port Mapping:** External ports are mapped to internal ports for each node, allowing external access to the various services provided by YugabyteDB.
- **Volume Mounting:** Persistent data storage is achieved through volume mounts, ensuring that data persists even if the containers are restarted or recreated.
- **Automatic Restart:** Containers are configured to restart unless explicitly stopped, maintaining the availability of the YugabyteDB cluster.
- **Joining Nodes:** Nodes `yugabytedb-node2` and `yugabytedb-node3` are configured to join `yugabytedb-node1` during startup, forming a three-node cluster.

**Usage:**

1. Create a custom network: `docker network create custom-network`
2. Execute `docker-compose up -d` to start the YugabyteDB cluster.
3. Access each node's YugabyteDB services via the specified external ports (e.g., `15433`, `15434`, `15435`).

This Docker Compose setup is designed for testing purposes, allowing developers and administrators to quickly deploy and evaluate a YugabyteDB cluster in a controlled environment.

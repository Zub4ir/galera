# MariaDB Galera

This is a MariaDB Galera Cluster using Docker. The Docker-Compose project is based off the official Docker image docs https://hub.docker.com/r/bitnami/mariadb-galera. I prefer creating a docker-compose project to accomodate additional project containers.

## To Run

```bash
# Navigate to root folder and run
docker-compose up --build -d
```

Check if all nodes are connected using client.

```
-- check cluster size. should be 3 for this setup
SHOW GLOBAL STATUS LIKE 'wsrep_cluster_size';
```

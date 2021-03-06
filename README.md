# MariaDB Galera

This is a MariaDB Galera Cluster using Docker. The Docker-Compose project is based off the official Docker image docs https://hub.docker.com/r/bitnami/mariadb-galera and this GitHub thread https://github.com/bitnami/bitnami-docker-mariadb-galera/issues/44. I prefer creating a docker-compose project to accomodate additional project containers.

_***Important notes in notes_

## To Run

If deployed locally, access on `localhost` via deafualt port 3306 to 3308 user "root" with password "pis12345" using a MariaDB/MySQL client such as [SQLyog Community](https://github.com/webyog/sqlyog-community/wiki/Downloads).

```bash
# Navigate to root folder and run
docker-compose up --build -d
```

Check if all nodes are connected using a client - should return 3 for this setup.

```
-- check cluster size. should be 3 for this setup
SHOW GLOBAL STATUS LIKE 'wsrep_cluster_size';
```

## Project Setup Notes

The project is created with a default `main` database on startup. I created a Dockerfile in a seperate folder to accomodate additional configs and startup scripts.

Please note the `wsrep_max_ws_size` limit of 2 Gibyte which limits your transaction size. If you require frequent large transactions, a Galera cluster is probably not the solution. I think the transaction limit is also enforced to ensure replication among the clusters remain fast.

https://www.percona.com/blog/2015/10/26/how-big-can-your-galera-transactions-be

Container restart functionality needs to looked into. Only possible to restart completely by rebuilding project from scratch (i.e. deleting containers, images and volumes).
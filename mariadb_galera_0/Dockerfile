FROM docker.io/bitnami/mariadb-galera:10.6

# on first execution the files with extensions .sh, .sql and .sql.gz located at /docker-entrypoint-initdb.d will executed (in container)
# seemingly, but didnt like it even with sleeping

# custom configs
COPY my_custom.cnf /opt/bitnami/mariadb/conf
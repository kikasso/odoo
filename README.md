[Odoo Official Image] (https://hub.docker.com/_/odoo/)

# Start Odoo instance
```shell
docker-compose up -d
```

# See
- [localhost:8069](http://localhost:8069/)
- [database/manager](http://localhost:8069/web/database/manager)

# Stop
```shell
docker-compose stop
```

# Install new community App / Module
```
1. Unzip module to the Odoo add-ons folder
2. Re-start Odoo
3. Turn on the developer mode > Update the apps list
4. Find the app and install it
```

# Update Odoo
```
docker-compose pull
docker-compose up -d --force-recreate
docker exec -it  odoo-web-1 bash
odoo --version
```


# Dump and Restore database
```
docker exec -t  odoo-db-1 pg_dump -U odoo odoo_test > ~/var/backup/odoo_test.sql

docker exec -i odoo-db-1 psql -U odoo -d postgres -c "SELECT pg_terminate_backend(pg_stat_activity.pid) FROM pg_stat_activity WHERE pg_stat_activity.datname = 'odoo_test' AND pid <> pg_backend_pid();" && \
docker exec -i odoo-db-1 psql -U odoo -d postgres -c "DROP DATABASE IF EXISTS odoo_test;" && \
docker exec -i odoo-db-1 psql -U odoo -d postgres -c "CREATE DATABASE odoo_test WITH OWNER odoo;" && \
docker exec -i  odoo-db-1 psql -U odoo -d odoo_test < ~/var/backup/odoo_test.sql
```
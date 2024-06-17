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
## Install odoo with docker compose

# clone source & build server

```bash
git clone https://github.com/erpblogs/odoo-docker.git --dept=1
cd odoo-docker
cp odoo-config/odoo-server.conf odoo-config/odoo.conf
sudo docker compose up -d
```

# Customize
> - Change the config file, docker-compose file and nginx file to update 
> - odoo-addons-customs this folder is using for your custom module
> - odoo-addons-3rd this folder is using for your 3rd module
> - odoo-ee this folder is using for odoo enterprise module

# System information
> - odoo-config/odoo-server.conf this file is example config for odoo server configuration
> - odoo-config/odoo.conf this file is example config for odoo configuration
> - odoo-nginx/default.conf this file is example config for nginx
> - default odoo admin username is admin and password is admin
> - default system admin password is odoo18@2024
> - postgres default username is odoo, password is odoo18@2024
> - database name default is odoo18
> - psql connect inside docker network odoo-network: psql -h postgres -U odoo -d odoo18 -p 5432
> - psql connect from localhost: psql -h localhost -U odoo -d odoo18 -p 5433
> - odoo-data is using for odoo data folder


# Go to web browser: 
[localhost](http://localhost)
[localhost:18069](http://localhost:18069)


## Odoo docker command 
# Restart Odoo service 
``` bash
sudo docker restart odoo18-web
#or 
sudo docker compose restart odoo18
```

**Checking odoo service**:

``` bash
docker exec -it odoo18-web /bin/bash -c "ps aux | grep odoo"
```

**Create an Odoo module**:
``` bash
docker exec -it odoo18-web /bin/bash -c "/usr/bin/python3 /usr/bin/odoo scaffold  module_name /mnt/extra-addons"
```

**Upgrade module from command an Odoo module**:
``` bash
docker exec -it odoo18-web /bin/bash -c "/usr/bin/python3 /usr/bin/odoo --db_host postgres --db_port 5432 --db_user odoo --db_password odoo18@2024 --http-port=9999 -d database_name -u module_name1,module_name2 --stop-after-init"
```

**Run command as a super user**:

``` bash
docker exec -it -U odoo18-web /bin/bash -c "ps aux | grep odoo"
```


## Install odoo with docker compose

# clone source & build server

```bash
git clone https://github.com/erpblogs/odoo-docker.git --dept=1
cd odoo-docker
mkdir odoo-addons-customs odoo-addons-3rd
# odoo-addons-customs this folder is using for your custom module
# odoo-addons-3rd this folder is using for your 3rd module
docker compose up -d
```

# Go to web browser: 
[localhost](http://localhost)
[localhost:18069](http://localhost:18069)

# Customize
Change the config file, docker-compose file and nginx file to update 
Add custom module on odoo-addons folder


## Odoo docker command 
# Restart Odoo service 
docker restart odoo18-web
or docker compose restart odoo18

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


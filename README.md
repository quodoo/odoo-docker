## Install odoo with docker compose

# clone source & build server

```bash
git clone https://github.com/erpblogs/odoo-docker.git --dept=1
cd odoo-docker 
docker compose up -d
```


# Go to web browser: 
[localhost](http://localhost)
[localhost:18069](http://localhost:18069)

# Customize
Change the config file, docker-compose file and nginx file to update 
Add custom module on odoo-addons folder
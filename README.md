# visualist_wp
Visualist (WordPress Upgrade)


## To install and launch The Visualist

You will need Docker installed and ready.

``` bash
docker-compose up
```

Then, in development, you should be able to launch `http://0.0.0.0` to view WordPress in all its glory.


## DigitalOcean

- [server setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04)
- [git setup](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-14-04)
- [docker setup](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04)
  Up through Step 4.
- [docker compose setup](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-14-04)
- [WordPress setup](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-and-phpmyadmin-with-docker-compose-on-ubuntu-14-04)
  I departed from some of the specific example stuff.

Data is installed in `/srv`.


## Database dump

``` bash
DATE=`date +%Y-%m-%dT%H:%M:%S%z` && \
  docker run -it --rm \
  --volumes-from visualist_wp_wordpress_1 \
  --network container:visualist_wp_wordpress_1 \
  wordpress:cli \
  db export /var/www/html/wp-content/exports/visualist_wp-$DATE.sql
```


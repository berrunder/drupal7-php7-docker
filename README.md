#Drupal 7 on php 7 with memcached

Docker-compose configuration to run Drupal 7 site on php7, nginx, mysql and memcached. PhpMyAdmin included.

Place site source under `source` and database sql dump under `data`. Execute `docker-compose up -d` to spin up containers.

Exposed ports:
- 8000 for http access to site
- 8100 for phpmyadmin

Database credentials can be changed in `docker-compose.yml`.

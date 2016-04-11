#Drupal 7 on php 7 with memcached

Docker-compose configuration to run Drupal 7 site on php7, nginx, mysql and memcached. PhpMyAdmin included.

Place site source under `source` and database sql dump under `data`. Execute `docker-compose up -d` to spin up containers.

Exposed ports:
- 8000 for http access to site
- 8100 for phpmyadmin

Database credentials can be changed in `docker-compose.yml`.

## Setting up drupal to use Mysql database and memcached

In `source/sites/default/settings.php`, set database credentials in `$databases['default']['default']`.

For Memcached, install `memcache` module and add following lines to settings.php:
```php
#change to path to memcache.inc from installed memcache module, if necessary
$conf['cache_backends'][] = 'sites/all/modules/contrib/memcache/memcache.inc';
$conf['cache_default_class'] = 'MemCacheDrupal';
$conf['cache_class_cache_form'] = 'DrupalDatabaseCache';
$conf['memcache_servers'] = array(
  'memcached:11211' => 'default',
);
```

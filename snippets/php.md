Deploying PHP apps with the uWSGI php plugin
--------------------------------------------

```ini
[uwsgi]
; load the required plugins, php is loaded as the default (0) modifier
plugins = 0:php

; our working dir (the DOCUMENT_ROOT of our instance)
project_dir = /var/www

; chdir to it (just for fun)
chdir = %(project_dir)

; check for static files in it
check-static = %(project_dir)
; ...but skip .php and .inc extensions
static-skip-ext = .php
static-skip-ext = .inc

; search for index.html when a dir is requested
static-index = index.html

; jail our php environment to project_dir
php-docroot = %(project_dir)

; ... and to the .php and .inc extensions
php-allowed-ext = .php
php-allowed-ext = .inc

; and search for index.php and index.inc if required
php-index = index.php
php-index = index.inc

; set php timezone
php-set = date.timezone=Europe/Rome

; use a max of 10 processes
processes = 10
; ...but start with only 2 and spawn the others on demand
cheaper = 2
```

remember to add the domain/ssl-domain/cluster-domain option and to tune the processes and cheaper values to your needs

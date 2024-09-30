## apache-php

Docker setup that builds very specific version of apache + php from source.

### Retrieving src 

- apache2
    - [Apache Archive](https://archive.apache.org/dist/httpd/)
    - `wget https://archive.apache.org/dist/httpd/httpd-X.X.XX.tar.gz`


- php 
    - [php.net](https://www.php.net/releases/)
    - `wget https://www.php.net/distributions/php-X.X.XX.tar.gz`

### Setup

- `httpd` will be installed under `/usr/local/apache2`
- `php` can be enabled by `LoadModule` Directive, `LoadModule php_module modules/libphp.so`

<br>

- `Dockerfile` provides the minimal configuration.
- Some httpd / php modules must be configured within each `./configure` command.
- Configuring other modules may require some package dependencies.

Створення Dockerfile
====================

- **Крок 1**
   - **Вказати , який буде базовий образ (наприклад, Ubuntu )**
   
   .. code-block:: ruby

      FROM ubuntu:latest

- **Крок 2**
   - **Встановлюємо всі необхідні сервіси та застосування, такі, як apache2 php7.0 curl pecl lynx-cur, потім встановлюється xdebug для того щоб була можливість відлагодження серверної частини, після чого ідуть необхідні налаштування xdebug.**
   
   .. code-block:: ruby
    
      RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive apt-get -y   install

      sudo apache2 php7.0 php7.0-mysql libapache2-mod-php7.0 php7.0-gd php7.0-mbstring curl pecl lynx-cur git

      && pecl install xdebug

      && rm -rf /tmp/pear

      && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)\n" >> /usr/local/etc/php/conf.d/xdebug.ini

      && echo "xdebug.idekey = PHPSTORM" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

      && echo "xdebug.default_enable = 0" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

      && echo "xdebug.remote_enable = 1" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

      && echo "xdebug.remote_autostart = 0" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

      && echo "xdebug.remote_connect_back = 0" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

      && echo "xdebug.profiler_enable = 0" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

      && echo "xdebug.remote_host = 10.254.254.254" >> /etc/php/7.0/fpm/conf.d/20-xdebug.ini

- **Крок 3**
    - **Вмикаємо модулі веб серверу Apache**
    
     .. code-block:: ruby
    
       RUN a2enmod php7.0

       RUN a2enmod
- **Крок 4**
    - **Налаштовуємо порти, через які можна буде отримати доступ до застосування, яке виконується всередині контейнера. В нашому випадку це порт 80 для протоколу HTTP, та порт 9000 для віддаленого відлагодження серверної частини**
    
     .. code-block:: ruby
    
       EXPOSE 80

       EXPOSE 9000
- **Крок 5**
   - **Приєднуємо три директорії, а також необхідні файли конфігурації:**
   
    .. code-block:: ruby
   
       ADD www /srv/www/testbed/htdocs

       ADD requests /srv/www/testbed/requests

       ADD opt /opt

       ADD sudoers.txt /etc/sudoers

       ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf
- **Крок 6**
   - **Команда для запуску веб серверу у фоновому режимі:**
   
    .. code-block:: ruby
    
       CMD /usr/sbin/apache2ctl -D FOREGROUND

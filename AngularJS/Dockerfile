#SUBINDO UM CONTAINER UBUNTU
FROM ubuntu:14.04
MAINTAINER Matheus Fidelis <matheus.fidelis@industriafox.com>

#INSTALANDO O AMBIENTE COMPLETO
RUN apt-get update ; apt-get install -y php5 libapache2-mod-php5 php5-cgi php5-cli php5-common php5-curl php5-dbg php5-dev php5-gd php5-gmp php5-json php5-ldap php5-odbc php5-pgsql php5-mysql php5-xmlrpc php5-xsl php5-enchant php5-intl libphp-jpgraph php-codesniffer php-doc php-http-request2 php5-adodb php5-imagick php5-imap php5-mcrypt php5-memcache php5-memcached php5-mongo php5-oauth phpunit php5-geoip php5-xdebug php5-exactimage php-pear firebird2.5-dev devscripts debget; apt-get clean ; /etc/init.d/apache2 start

#ADICIONANDO A PASTA SRC PARA O APACHE DO CONTAINER 
RUN rm -rf /var/www/html*
ADD src /var/www/html

#CRIANDO UM VOLUME
VOLUME /var/www/html/

#VARIÁVEIS DE AMBIENTE
RUN a2enmod rewrite
RUN chown -R www-data:www-data /var/www
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

#EXPOSE DE PORTA
EXPOSE 80

#COMANDO DURANTE A INICIALIZAÇÃO - START NO APACHE
CMD ["/usr/sbin/apache2", "-D",  "FOREGROUND"]

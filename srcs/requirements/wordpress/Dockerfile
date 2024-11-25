FROM alpine:3.19

WORKDIR /var/www/wordpress/

RUN	apk update && \
	apk upgrade && \
	apk add fcgi wget php83 php83-fpm php83-phar php83-iconv php83-mysqli mariadb-client shadow && \
	wget --output-document=/usr/local/bin/wp https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && \
	chmod +x /usr/local/bin/wp && \
	groupmod www-data && \
	useradd --home-dir /home/www-data --create-home --no-user-group --system www-data && \
	chown --recursive www-data:www-data /var/www/wordpress/ /var/log/php83 && \
	rm -rf /var/cache/apk/*

COPY conf/php-fpm.conf /etc/php83/php-fpm.conf
COPY tools/wordpress-entrypoint.sh /tools/wordpress-entrypoint.sh

RUN chmod -R 755 /tools

EXPOSE 9000

ENTRYPOINT ["/tools/wordpress-entrypoint.sh"]

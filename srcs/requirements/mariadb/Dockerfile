FROM alpine:3.19

RUN apk update && apk add --no-cache mariadb mariadb-client mariadb-server-utils gettext && \
	rm -f /var/cache/apk/*

COPY conf/mariadb-server.cnf /etc/mysql/my.cnf
COPY tools/mariadb.sql /tools/mariadb.sql
COPY tools/mariadb-entrypoint.sh /tools/mariadb-entrypoint.sh

RUN chmod -R 755 /tools

EXPOSE 3306

ENTRYPOINT ["/tools/mariadb-entrypoint.sh"]

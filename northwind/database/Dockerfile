FROM mysql:5.7

# set the password to changeit
ENV MYSQL_ROOT_PASSWORD=changeit

# write one or more Docker commands/directives to copy the *.sql files into /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

# add healthcheck - v2
HEALTHCHECK --interval=60s --timeout=30s --start-period=15s --retries=3 \
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

# where MySQL stores the database
VOLUME /var/lib/mysql

# build the image
# run the image
# exec in and run mysql -uroot -pchangeit

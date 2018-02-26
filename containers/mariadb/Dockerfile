FROM mariadb:latest

COPY ./data/db/init.d/ /docker-entrypoint-initdb.d/

RUN echo mysqld: ALL: allow >> /etc/hosts.allow

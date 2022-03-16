FROM mariadb:10.1.38

LABEL maintainer="Konstantin Prishvin <kostya.php@gmail.com>"

COPY my.cnf /etc/mysql/conf.d/my.cnf

RUN chmod -R 644 /etc/mysql/conf.d/my.cnf

EXPOSE 3306

CMD ["mysqld"]

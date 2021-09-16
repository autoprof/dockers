FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update && \
	apt-get install -y mariadb-server-10.3 && \
	rm -rf /var/lib/apt/lists/* && \
	sed -i 's/bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/g' /etc/mysql/mariadb.conf.d/50-server.cnf

RUN \
	/etc/init.d/mysql start && \
	mysql -e "CREATE USER 'root'@'%' IDENTIFIED BY 'root';" && \
	mysql -e "GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION" && \
	mysql -e "FLUSH PRIVILEGES" && \
	echo "User creation OK";


EXPOSE 3306

CMD ["/usr/bin/mysqld_safe"]


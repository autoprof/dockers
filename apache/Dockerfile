FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update && \
	apt-get install -y php php-xml php-mysqli php-mbstring unzip wget && \
	rm /var/www/html/index.html && \
	rm -rf /var/lib/apt/lists/*


WORKDIR /var/www/html/

RUN \
	wget "https://files.phpmyadmin.net/phpMyAdmin/5.1.1/phpMyAdmin-5.1.1-all-languages.zip" && \
	unzip phpMyAdmin-5.1.1-all-languages.zip && \
	rm phpMyAdmin-5.1.1-all-languages.zip && \
	mv phpMyAdmin-5.1.1-all-languages/* . && \
	rmdir phpMyAdmin-5.1.1-all-languages

COPY config.inc.php ./

RUN chmod 0555 config.inc.php

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]

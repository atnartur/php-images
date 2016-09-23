FROM php:7.0.11-fpm

MAINTAINER Artur Atnagulov <i@atnartur.ru>

RUN apt-get update && \
	apt-get install git -y && \

	docker-php-ext-install pdo_mysql && \

	git clone --depth=1 git://github.com/phalcon/cphalcon.git && \ 
	cd cphalcon && \
	git fetch --tags && \
	git checkout v3.0.1 && \
	cd build && \
	./install && \

	cd ../../ && \
	rm -r cphalcon && \
	apt-get purge git -y && \
	apt-get clean && \
	rm -r /var/lib/apt/lists/*

COPY ./phalcon.ini /usr/local/etc/php/conf.d/
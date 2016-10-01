FROM php:7.0.11-fpm

MAINTAINER Artur Atnagulov <i@atnartur.ru>

RUN apt-get update && \
	apt-get install \
		git \ 
		libpq-dev \ 
		zlib1g-dev \
		-y --no-install-recommends && \

	docker-php-ext-install \
		pdo_pgsql \
		pdo_mysql \
		zip && \

	git clone --depth=1 git://github.com/phalcon/cphalcon.git && \ 
	cd cphalcon && \
	git fetch --tags && \
	git checkout v3.0.1 && \
	cd build && \
	./install && \

	cd ../../ && \
	rm -r cphalcon && \
	apt-get clean && \
	rm -r /var/lib/apt/lists/*

COPY ./phalcon.ini /usr/local/etc/php/conf.d/
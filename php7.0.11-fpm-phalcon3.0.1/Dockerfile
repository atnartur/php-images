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

	git clone -b v3.0.1 --single-branch git://github.com/phalcon/cphalcon.git && \ 
	cd cphalcon/build && \
	./install && \
	docker-php-ext-enable phalcon && \

	cd ../../ && \
	rm -r cphalcon && \
	apt-get clean && \
	rm -r /var/lib/apt/lists/*
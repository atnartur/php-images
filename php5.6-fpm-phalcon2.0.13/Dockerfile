FROM php:5.6-fpm

MAINTAINER Artur Atnagulov <i@atnartur.ru>

RUN apt-get update && \
	apt-get install git -y && \

	docker-php-ext-install pdo_mysql && \

	git clone -b phalcon-v2.0.13 --single-branch git://github.com/phalcon/cphalcon.git && \ 
	cd cphalcon/build && \
	./install && \
	docker-php-ext-enable phalcon && \

	cd ../../ && \
	rm -r cphalcon && \
	apt-get clean && \
	rm -r /var/lib/apt/lists/*
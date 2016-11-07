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

	docker-php-ext-enable \
		pdo_pgsql \
		pdo_mysql \
		zip && \

	apt-get clean && \
	rm -r /var/lib/apt/lists/*

RUN git clone -b v3.0.1 --single-branch git://github.com/phalcon/cphalcon.git && \ 
	cd cphalcon/build && \
	sed -i 's/-march=native/-march=x86-64/g' install && \
	sed -i 's/-mtune=native/-mtune=generic/g' install && \

	echo '#!/bin/sh\n\
-march=x86-64 -mtune=generic'\
>> gcccpuopt && \
	# cat 'gcccpuopt\
	# echo "-march=x86-64 -mtune=generic"' && \
	./install && \
	docker-php-ext-enable phalcon && \

	cd ../../ && \
	rm -r cphalcon
	
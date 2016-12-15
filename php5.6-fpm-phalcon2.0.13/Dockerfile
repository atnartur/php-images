FROM php:5.6-fpm

MAINTAINER Artur Atnagulov <i@atnartur.ru>

RUN apt-get update && \
	apt-get install zlib1g-dev git -y && \

	docker-php-ext-install pdo_mysql zip && \

	git clone -b phalcon-v2.0.13 --single-branch git://github.com/phalcon/cphalcon.git && \ 
	cd cphalcon/build && \
	sed -i 's/-march=native/-march=x86-64/g' install && \
	sed -i 's/-mtune=native/-mtune=generic/g' install && \

	echo '#!/bin/sh\n\
-march=x86-64 -mtune=generic'\
>> gcccpuopt && \
	./install && \
	docker-php-ext-enable phalcon && \

	cd ../../ && \
	rm -r cphalcon && \
	apt-get clean && \
	rm -r /var/lib/apt/lists/*
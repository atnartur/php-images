FROM php:5.6-fpm

MAINTAINER Artur Atnagulov <i@atnartur.ru>

RUN apt-get update && \
	apt-get install git -y && \
	git clone --depth=1 git://github.com/phalcon/cphalcon.git && \ 
	cd cphalcon && \
	git fetch --tags && \
	git checkout phalcon-v2.0.13 && \
	cd build && \
	./install && \
	cd ../../ && \
	rm -r cphalcon && \
	apt-get purge git -y && \
	rm -r /var/lib/apt/lists/*
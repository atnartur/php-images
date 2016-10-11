FROM php:5.6-fpm

MAINTAINER Artur Atnagulov <i@atnartur.ru>

RUN apt-get update && \
	apt-get install libcurl4-gnutls-dev git -y mysql-client libmysqlclient-dev && \
	docker-php-ext-install pdo_mysql curl mysqli mysql && \
	apt-get clean && \
	rm -r /var/lib/apt/lists/*

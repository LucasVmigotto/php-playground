FROM php:8-apache

RUN apt-get install bash

ENV GOSU_VERSION 1.10
RUN curl -sS -Lo /usr/bin/gosu https://github.com/tianon/gosu/releases/download/$GOSU_VERSION/gosu-amd64
RUN chmod +x /usr/bin/gosu

ENV TZ=America/Sao_Paulo
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV GIST_URL https://gist.githubusercontent.com/LucasVmigotto/c10ed96848c8b446f48aa866a0ca5e19/raw/da6a338cb8d7ab7bd7f2cdb1c03434d5dde4ce02/entrypoint-php.sh
RUN curl -sS $GIST_URL > /usr/bin/entrypoint.sh
RUN chmod +x /usr/bin/entrypoint.sh

VOLUME /app
WORKDIR /app

ENTRYPOINT [ "/usr/bin/entrypoint.sh" ]
CMD [ php ]

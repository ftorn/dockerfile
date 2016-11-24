FROM debian

MAINTAINER ft

ENV DEBIAN_FRONTEND noninteractive
ENV C_FORCE_ROOT root

RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10 && \
    echo 'deb http://downloads-distro.mongodb.org/repo/debian-sysvinit dist 10gen' | tee /etc/apt/sources.list.d/mongodb.list && \
    apt-get update && \
    apt-get install -y mongodb-org vim git supervisor libxml2-dev python-dev python-pip libxslt-dev libz-dev wget && \
    wget -O- https://www.rabbitmq.com/rabbitmq-release-signing-key.asc | apt-key add - && \
    echo 'deb http://www.rabbitmq.com/debian/ testing main' | tee /etc/apt/sources.list.d/rabbitmq.list && \
    apt-get update && \
    apt-get -y install rabbitmq-server

RUN git clone https://github.com/upgoingstar/datasploit.git && \
    cd datasploit && \
    pip install -U pip && \
    pip install -r requirements.txt && \
    mkdir -p /var/log/supervisor && \ 
    mkdir /datasploitDb

COPY mongod.conf /etc/mongod.conf
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY config.py /datasploit/

CMD ["/usr/bin/supervisord"]

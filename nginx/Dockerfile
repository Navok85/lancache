#################################################
#
# Image erzeugen mit:
# $ docker build -t lancache/nginx .
#
# Confis nach /pool1/nginx kopieren
# $ mkdir -p /pool1/nginx
#
# Speicherort für den Cache anlegen (hier: /pool1/lancache)
# $ mkdir -p /pool1/lancache/data/blizzard/
# $ mkdir -p /pool1/lancache/data/microsoft/
# $ mkdir -p /pool1/lancache/data/steam/
# $ mkdir -p /pool1/lancache/data/origin/
# $ mkdir -p /pool1/lancache/data/installs/
# $ mkdir -p /pool1/lancache/data/other/
# $ mkdir -p /pool1/lancache/logs/Errors
# $ mkdir -p /pool1/lancache/logs/Keys
# $ mkdir -p /pool1/lancache/logs/Access
#
# Container starten/erzeugen mit:
# $ docker run -d \
#              --name=lancache-nginx 
#              -v /pool1/lancache:/srv/lancache 
#              -v /pool1/nginx:/etc/nginx/ 
#              --net=host lancache/nginx
#
#################################################


FROM ubuntu
MAINTAINER [cXt]Navok - Marcel Veit

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install build-essential \
		    libpcre3 \
                    libpcre3-dev \
                    zlib1g-dev \
                    libreadline-dev \
                    libncurses5-dev \
                    libssl-dev \
                    wget \
                 -y && \
    cd /tmp && \
    wget http://nginx.org/download/nginx-1.13.8.tar.gz && \
    tar xzf nginx-1.13.8.tar.gz && \
    cd /tmp/nginx-1.13.8 && \
    ./configure --prefix=/etc/nginx \
                --sbin-path=/usr/sbin/nginx \
                --conf-path=/etc/nginx/nginx.conf \
                --error-log-path=/var/log/nginx/error.log \
                --http-log-path=/var/log/nginx/access.log \
                --pid-path=/var/run/nginx.pid \
                --lock-path=/var/run/nginx.lock \
                --with-http_sub_module \
                --with-http_ssl_module \
                --with-http_slice_module \
                --with-file-aio \
                --with-threads && \
    make && \
    make install && \
    cd / && \
    rm /tmp/* -R && \
    apt-get remove -y build-essential wget --purge && \
    apt-get autoremove --purge -y && \
    apt-get clean

VOLUME ["/pool1","/etc/nginx"]

CMD ["nginx", "-g", "daemon off;"]

#################################################
#
# Image erzeugen mit:
# $ docker build -t lancache/sniproxy .
#
# Config sniproxy.conf nach /srv/sniproxy kopieren
# $ mkdir -p /pool1/sniproxy
#
# Container starten/erzeugen mit:
# $ docker run -d \
#              --name lancache-sniproxy \
#              --net=host \
#              -v /pool1/sniproxy/sniproxy.conf:/etc/sniproxy/sniproxy.conf \
#              lancache/sniproxy 
#
#################################################

FROM ubuntu
MAINTAINER [cXt]Navok - Marcel Veit

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y autotools-dev \
                       cdbs \
                       debhelper \
                       dh-autoreconf \
                       dpkg-dev \
                       gettext \
                       libev-dev \
                       libpcre3-dev \
                       libudns-dev \
                       pkg-config \
                       fakeroot \
                       devscripts \
                       git && \
    mkdir /tmp/sniproxy && \
    cd /tmp/sniproxy && \
    git clone https://github.com/dlundquist/sniproxy . && \
    ./autogen.sh && dpkg-buildpackage && \
    dpkg -i ../sniproxy_*.deb && \
    rm /tmp/* -R && \
    apt-get remove -y autotools-dev \
                      cdbs \
                      debhelper \
                      dh-autoreconf \
                      dpkg-dev \
                      gettext \
                      libev-dev \
                      libpcre3-dev \
                      libudns-dev \
                      pkg-config \
                      fakeroot \
                      devscripts \
                      git \
                   --purge && \
    apt-get autoremove --purge -y && \
    apt-get clean 

CMD ["/usr/sbin/sniproxy","-f","-c","/etc/sniproxy/sniproxy.conf"]

#################################################
# Create docker image:
# $ docker build -t lancache/unbound .
#
# Copy unbound.conf to /srv/unbound
# $ mkdir -p /pool1/unbound
#
# Container start:
# $ docker run -d \
#              --name="lancache-unbound" \
#              --net=host \
#              -v /pool1/unbound/unbound.conf:/etc/unbound/unbound.conf \
#              lancache/unbound

FROM ubuntu
MAINTAINER [cXt]Navok - Marcel Veit

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install unbound -y && \
    apt-get clean

CMD ["/usr/sbin/unbound", "-d"]

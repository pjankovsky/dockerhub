FROM ubuntu:bionic

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get -y install certbot \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV EMAIL admin@localhost
ENV DOMAINS localhost

LABEL Description="Run like: docker run -e EMAIL=email@domain -e DOMAINS=domain.tld -v /etc/letsencrypt/:/etc/letsencrypt/ -p 80:80 peterjankovsky/letsencrypt"

CMD certbot certonly --non-interactive --agree-tos --standalone -d ${DOMAINS} -m ${EMAIL}

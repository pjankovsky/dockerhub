FROM mprasil/bitwarden

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get -y install certbot \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV LE_EMAIL peter@jankovsky.me
ENV LE_DOMAIN pw1.jankovsky.me

ENV ROCKET_TLS '{certs="/etc/letsencrypt/live/${LE_DOMAIN}/fullchain.pem",key="/etc/letsencrypt/live/${LE_DOMAIN}/privkey.pem"}'
ENV DOMAIN https://${LE_DOMAIN}

CMD certbot certonly --non-interactive --agree-tos --standalone -d ${LE_DOMAIN} -m ${LE_EMAIL} \
 && ./bitwarden_rs

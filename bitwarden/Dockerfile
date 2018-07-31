FROM peterjankovsky/letsencrypt as cert

ENV LE_EMAIL peter@jankovsky.me
ENV LE_DOMAIN pw1.jankovsky.me

RUN certbot certonly --non-interactive --agree-tos --standalone -d ${LE_DOMAIN} -m ${LE_EMAIL}

FROM mprasil/bitwarden

RUN mkdir /ssl
COPY --from=cert /etc/letsencrypt/live/${LE_DOMAIN} /ssl

ENV ROCKET_TLS '{certs="/ssl/fullchain.pem",key="/ssl/privkey.pem"}'
ENV DOMAIN https://${LE_DOMAIN}

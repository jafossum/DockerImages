FROM resin/rpi-raspbian:stretch

LABEL maintainer="John A. Fossum <jafossum@gmail.com>"

RUN apt update \
	&& apt install -y ca-certificates nginx \
        && rm -rf /var/lib/apt/lists/*

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

COPY ./nginx_conf/secret /etc/nginx/sites-available/homeassistant.conf

# Disable default conf and add homeassistant.conf symlink
RUN cd /etc/nginx/sites-enabled \
    && unlink default \
    && ln -s /etc/nginx/sites-available/homeassistant.conf homeassistant.conf

EXPOSE 80 443

ENTRYPOINT ["nginx"]

CMD ["-g", "daemon off;"]

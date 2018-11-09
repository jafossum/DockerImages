FROM resin/rpi-raspbian:stretch

LABEL maintainer="John A. Fossum <jafossum@gmail.com>"

RUN apt update \
        && apt install -y certbot \
        && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["certbot"]

CMD ["renew"]

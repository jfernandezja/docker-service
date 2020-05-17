FROM debian

RUN set -x \
    && apt update -y \
    && apt upgrade -y \
    && apt install curl nginx -y

COPY reverse-proxy.conf /etc/nginx/sites-available/reverse-proxy.conf

RUN unlink /etc/nginx/sites-enabled/default \
    && ln -s /etc/nginx/sites-available/reverse-proxy.conf /etc/nginx/sites-enabled/reverse-proxy.conf \
    && rm -f /var/www/html/index.nginx-debian.html

HEALTHCHECK --interval=30s \
    CMD curl -f http://localhost || exit 1

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
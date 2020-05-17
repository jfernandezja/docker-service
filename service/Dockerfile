FROM debian

RUN set -x \
    && apt update -y \
    && apt upgrade -y \
    && apt install curl nginx -y

COPY index.html /var/www/html/index.nginx-debian.html

HEALTHCHECK --interval=30s \
    CMD curl -f http://localhost || exit 1

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p ilyaerofeev.com/img && \
    chmod -R 754 /var/www/ilyaerofeev.com/ && \
    useradd Egor && groupadd Erofeev && usermod -aG Erofeev Egor && \
    chown -R Egor:Erofeev /var/www/ilyaerofeev.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/ilyaerofeev.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Egor/g' /etc/nginx/nginx.conf
ADD index.html /var/www/ilyaerofeev.com/
ADD img.jpg /var/www/ilyaerofeev.com/img/
CMD ["nginx", "-g", "daemon off;"]

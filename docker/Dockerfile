FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p antonyakynov.com/img && \
    chmod -R 754 /var/www/antonyakynov.com/ && \
    useradd anton && groupadd yakynov && usermod -aG anton yakynov && \
    chown -R anton:yakynov /var/www/antonyakynov.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/antonyakynov.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user anton/g' /etc/nginx/nginx.conf
ADD index.html /var/www/antonyakynov.com/
ADD img.jpg /var/www/antonyakynov.com/img/
CMD ["nginx", "-g", "daemon off;"]

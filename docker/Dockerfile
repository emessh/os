FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p DmitriyEmeshov.com/img && \
    chmod -R 754 /var/www/dmitriyemeshov.com/ && \
    useradd Dmitriy && groupadd Emeshov && usermod -aG Emeshov Dmitriy && \
    chown -R Dmitriy:Emeshov /var/www/dmitriyemeshov.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/dmitriyemeshov.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Dmitriy/g' /etc/nginx/nginx.conf
ADD index.html /var/www/dmitriyemeshov.com/
ADD img.jpg /var/www/dmitriyemeshov.com/img/
CMD ["nginx", "-g", "daemon off;"]
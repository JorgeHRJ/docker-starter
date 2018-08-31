# Base from Amazon Linux
FROM amazonlinux:2017.09

MAINTAINER Jorge Hernández Ríos <jorgehrios94@gmail.com>

# Install packages
RUN yum install -y nginx

# Install NodeJS
RUN curl -sL https://rpm.nodesource.com/setup_10.x | bash -
RUN yum install -y nodejs
RUN npm install npm@4.4.1 -g

# Create App User
RUN groupadd -g 33 -o app
RUN useradd -d /home/app -u 33 -g 33 -s /sbin/nologin app

# Configure Nginx
RUN rm -f /etc/nginx/conf.d/virtual.conf
RUN chown app:app -R /var/lib/nginx
COPY etc/nginx/nginx.conf /etc/nginx/
COPY etc/nginx/conf.d/ /etc/nginx/conf.d/
COPY etc/nginx/.htpasswd /etc/nginx/

# Expose HTTP
EXPOSE 80

# Run
WORKDIR /home/app

CMD nginx

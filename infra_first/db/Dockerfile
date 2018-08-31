# Base from Ubuntu LTS version
FROM ubuntu:16.04

MAINTAINER Jorge Hernández Ríos <jorgehrios94@gmail.com>

# APT updates and basic utils install
RUN apt-get update -y && apt-get upgrade -y && apt-get install -y apt-utils vim curl unzip git

# MySQL password setup
RUN echo mysql-server mysql-server/root_password password root | debconf-set-selections
RUN echo mysql-server mysql-server/root_password_again password root | debconf-set-selections

# MySQL installation
RUN apt-get install -y mysql-server mysql-client

# Permissions
RUN usermod -d /var/lib/mysql/ mysql
RUN mkdir /var/run/mysqld
RUN chown mysql /var/run/mysqld

# MySQL setup
ADD config/mysqld.cnf /etc/mysql/mysql.conf.d/
COPY config/my.cnf /root/.my.cnf

# Use database dump (add it first to data and then uncomment line above)
#COPY data/yourdump.sql /root/

# Expose
EXPOSE 3306

# Run
CMD ["mysqld"]


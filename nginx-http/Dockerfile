# Debian: Nginx 1.9.9 (HTTP)
#
# VERSION 0.0.1

#
# Pull the base image.
#
FROM debian:jessie

#
# Set the author.
#
MAINTAINER Eric Mugerwa <dev@ericmugerwa.com>

#
# Add nginx repository.
#
RUN apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62
RUN echo "deb http://nginx.org/packages/mainline/debian/ jessie nginx" >> /etc/apt/sources.list

#
# Set NGINX_Version environment variable.
#
ENV NGINX_VERSION 1.9.9-1~jessie

#
# Update apt and install:
# 
# 	- openssl
# 	- ca-certificates
# 	- nginx
# 
# Remove "/var/lib/apt/lists/*".
#
RUN apt-get update && \
    apt-get install -y openssl ca-certificates nginx=${NGINX_VERSION} && \
    rm -rf /var/lib/apt/lists/*

#
# Add managed nginx.conf.
#
ADD files/etc/nginx/nginx.conf /etc/nginx/nginx.conf

#
# Remove default /etc/nginx/conf.d/*.
#
RUN rm -rf /etc/nginx/conf.d/*

#
# Add managed /etc/nginx/conf.d/default.conf.
#
ADD files/etc/nginx/conf.d/default.conf /etc/nginx/conf.d/default.conf

#
# Remove `/var/www/*`.
#
RUN rm -rf /var/www/*

#
# Forward request and error logs to docker log collector.
#
RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/stderr /var/log/nginx/error.log

#
# Define mountable directories.
#
VOLUME ["/etc/nginx", "/var/www", "/var/cache/nginx"]

#
# Listen on HTTP and HTTPS ports.
#
EXPOSE 80 443

#
# Configure executable to start nginx.
#
ENTRYPOINT ["nginx"]

#
# Define default command.
#
CMD []

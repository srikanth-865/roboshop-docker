FROM nginx:1.24.0-alpine3.17-slim
#we dont require nginx webpage we use roboshop webpage 
RUN rm -rf /usr/share/nginx/html/ && \
#we remove the default one and i ll provide our roboshop configurations
    rm -rf /etc/nginx/nginx.conf && \
    #we remove it because we don't want the default server configuration interfering with our roboshop API  configuration.
    rm -rf /etc/nginx/conf.d/default.conf
RUN mkdir -p /var/cache/nginx/client_temp && \
    mkdir -p /var/cache/nginx/proxy_temp && \
    mkdir -p /var/cache/nginx/fastcgi_temp && \
    mkdir -p /var/cache/nginx/uwsgi_temp && \
    mkdir -p /var/cache/nginx/scgi_temp && \
    #we make nginx as user/group the owner of /var/cache/nginx
    chown -R nginx:nginx /var/cache/nginx && \
    #this also we make as nginx user run for /etc/nginx/ && \
    chown -R nginx:nginx /etc/nginx/ && \
    #So Nginx can access the configuration files/directories. with read write execute
    chmod -R 755 /etc/nginx/ && \
    #we making nginx as owner so the process can work with these files/directories without running as root
    chown -R nginx:nginx /var/log/nginx

#This is intended for SSL/TLS-related files such as certificates and keys.
RUN mkdir -p /etc/nginx/ssl/ && \
    chown -R nginx:nginx /etc/nginx/ssl/ && \
    chmod -R 755 /etc/nginx/ssl/

RUN touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid /run/nginx.pid
COPY static/ /usr/share/nginx/html/
COPY nginx.conf /etc/nginx/nginx.conf
USER nginx
CMD ["nginx", "-g", "daemon off;"]




#first time running without change os anything 
# FROM nginx:1.24.0
# RUN rm -rf /usr/share/nginx/html/*
# RUN rm -rf /etc/nginx/nginx.conf
# RUN rm -rf /etc/nginx/conf.d/default.conf
# COPY static/ /usr/share/nginx/html/
# COPY nginx.conf /etc/nginx/nginx.conf
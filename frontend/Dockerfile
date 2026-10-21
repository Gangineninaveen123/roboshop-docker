FROM nginx

# Commands to run
RUN rm -rf /usr/share/nginx/html/index.html

RUN rm -rf /etc/nginx/nginx.conf

# copying files
ADD nginx.conf /etc/nginx/nginx.conf
ADD static/ /usr/share/nginx/html/
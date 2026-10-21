FROM nginx

# Commands to run
RUN rm -rf /usr/share/nginx/html/index.html

RUN rm -rf /etc/nginx/nginx.conf
# expecially docker images lo, nginx.conf ni konii sarlu, [/etc/nginx/conf.d/default.conf] vachi ovveride chese chance vundi, so [/etc/nginx/conf.d/default.conf]-> deeni kuda remove chestunna.
RUN rm -rf /etc/nginx/conf.d/default.conf

# copying files
ADD nginx.conf /etc/nginx/nginx.conf
ADD static /usr/share/nginx/html/
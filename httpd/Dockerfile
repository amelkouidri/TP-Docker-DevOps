FROM httpd:2.4

COPY index.html /usr/local/apache2/htdocs/

RUN echo '\n\
LoadModule proxy_module modules/mod_proxy.so\n\
LoadModule proxy_http_module modules/mod_proxy_http.so\n\
<VirtualHost *:80>\n\
    ProxyPreserveHost On\n\
    ProxyPass /api/ http://backend:8080/\n\
    ProxyPassReverse /api/ http://backend:8080/\n\
    ProxyPass / http://frontend:80/\n\
    ProxyPassReverse / http://frontend:80/\n\
</VirtualHost>' >> /usr/local/apache2/conf/httpd.conf
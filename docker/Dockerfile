FROM nginx

# Copying the configuration and html files inside docker image
COPY *.conf /etc/nginx/conf.d/
COPY *.html /usr/share/nginx/html/

# Creating necessary directories and symlinks as per requirement
RUN mkdir -p /usr/share/nginx/firstpage/html /usr/share/nginx/secondpage/html /usr/share/nginx/thirdpage/html
RUN ln -s /usr/share/nginx/html/1.html /usr/share/nginx/firstpage/html/index.html
RUN ln -s /usr/share/nginx/html/2.html /usr/share/nginx/secondpage/html/index.html
RUN ln -s /usr/share/nginx/html/3.html /usr/share/nginx/thirdpage/html/index.html

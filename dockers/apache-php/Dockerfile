FROM --platform=linux/amd64 ubuntu:24.04

RUN apt update

RUN apt install -y build-essential autoconf libtool bison re2c pkg-config \
                   libssl-dev libexpat-dev libpcre3-dev libapr1-dev libaprutil1-dev \
                   libxml2-dev libsqlite3-dev

RUN mkdir /ap-src/

COPY httpd-2.4.60.tar.gz /ap-src/httpd-2.4.60.tar.gz
COPY php-8.3.12.tar.gz /ap-src/php-8.3.12.tar.gz

WORKDIR /ap-src/
RUN tar -xzf httpd-2.4.60.tar.gz && tar -zxf php-8.3.12.tar.gz
RUN cd httpd-2.4.60 && ./configure --enable-so \ 
    && make -j $(nproc) && make install
RUN cd php-8.3.12 && ./configure --with-apxs2=/usr/local/apache2/bin/apxs \
    && make -j $(nproc) && make install

CMD ["/usr/local/apache2/bin/apachectl", "-D", "FOREGROUND"]
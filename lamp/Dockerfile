FROM centos
RUN yum install -y epel-release
RUN yum install -y nginx
RUN yum install -y gcc automake autoconf libtool make
RUN yum install -y libxml2-devel gd-devel libmcrypt-devel libcurl-devel openssl-devel
RUN yum install -y php-mysql php-pdo php-fpm
RUN yum install -y php-redis
RUN yum install -y wget
RUN wget http://cn2.php.net/distributions/php-5.6.12.tar.xz
RUN xz -d php-5.6.12.tar.xz
RUN tar -xvf php-5.6.12.tar
RUN cd php-5.6.12 && ./configure  --enable-shared --with-libxml-dir --with-gd --with-openssl --enable-mbstring --with-mcrypt --with-mysqli --with-mysql --enable-opcache --enable-mysqlnd --enable-zip --with-zlib-dir --with-pdo-mysql --with-jpeg-dir --with-freetype-dir --with-curl --without-pdo-sqlite --without-sqlite3
RUN cd php-5.6.12 && make
RUN cd php-5.6.12 && make install
ADD nginx/nginx.conf /etc/nginx/
ADD nginx/zfblog.conf /etc/nginx/conf.d/
ADD php-fpm/www.conf /etc/php-fpm.d/
ADD nginx/myadmin.conf /etc/nginx/conf.d/
RUN groupadd www
RUN useradd www -g www
RUN yum install -y php-mbstring
RUN chown -R www:www /var/lib/nginx
RUN cd /var/lib/php/ && mkdir session
RUN chown -R www:www /var/lib/php
ADD start.sh /home/start.sh
ENV PATH /home:$PATH
EXPOSE 80
CMD ["start.sh"]


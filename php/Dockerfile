FROM centos
RUN yum update -y
RUN yum install -y epel-release
RUN yum install -y gcc automake autoconf libtool make
RUN yum install -y libxml2-devel gd-devel libmcrypt-devel libcurl-devel openssl-devel
#RUN yum install -y php-mysql php-pdo php-fpm
RUN yum install -y php-mysql php-pdo
RUN yum install -y wget
RUN yum install -y php-gd
RUN yum install -y php-mcrypt
#RUN wget http://cn2.php.net/distributions/php-5.6.12.tar.xz
#ENV PHP_VERSION php-7.0.0RC3
ENV PHP_VERSION php-7.0.0RC5
RUN wget https://downloads.php.net/~ab/$PHP_VERSION.tar.xz
RUN xz -d $PHP_VERSION.tar.xz
RUN tar -xvf $PHP_VERSION.tar
RUN cd $PHP_VERSION && ./configure --prefix=/usr/local/php --with-config-file-path=/usr/local/php/etc --enable-fpm --enable-shared --with-libxml-dir --with--mysql --with-gd --with-openssl --enable-mbstring --with-mcrypt --with-mysqli --enable-opcache --enable-mysqlnd --enable-zip --with-zlib-dir --with-pdo-mysql --with-jpeg-dir --with-freetype-dir --with-curl --without-pdo-sqlite --without-sqlite3
RUN cd $PHP_VERSION && make
RUN cd $PHP_VERSION && make install
RUN mv /usr/local/php/etc/php-fpm.conf.default /usr/local/php/etc/php-fpm.conf
RUN ln -s /usr/local/php/sbin/php-fpm /usr/sbin/php-fpm
RUN cat /usr/local/php/etc/php-fpm.d/www.conf.default
RUN groupadd www
RUN useradd www -g www
RUN yum clean all
#RUN yum install -y php-mbstring
#RUN yum install -y php-redis
RUN cd /var/lib/php/ && mkdir session
RUN chown -R www:www /var/lib/php
#RUN yum install -y supervisor
#RUN mkdir -p /var/run/sshd
#RUN mkdir -p /var/log/supervisor
#ADD supervisord.conf /etc/supervisord.conf
#CMD ["/usr/bin/supervisord"]
CMD ["php-fpm"]


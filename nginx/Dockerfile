FROM centos
RUN yum install -y epel-release && \
	yum install -y nginx && \
	groupadd www && \
	useradd www -g www && \
	chown -R www:www /var/lib/nginx
ADD nginx.conf /etc/nginx/
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

CMD ["nginx"]
EXPOSE 80 



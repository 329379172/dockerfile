FROM centos
#RUN yum install -y wget
#RUN yum install -y gcc automake autoconf libtool make
#RUN yum install -y gcc-c++ 
#RUN wget https://nodejs.org/dist/v0.12.7/node-v0.12.7.tar.gz
#RUN tar zxvf node-v0.12.7.tar.gz
#RUN rm -f node-v0.12.7.tar.gz
#RUN cd node-v0.12.7 && ./configure
#RUN cd node-v0.12.7 && make
#RUN cd node-v0.12.7 && make install
#EXPOSE 80
RUN yum install -y epel-release
RUN yum install -y nodejs
RUN yum install -y npm
RUN npm install -g pm2

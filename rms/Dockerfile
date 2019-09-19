FROM centos:7.4.1708

WORKDIR /home1
WORKDIR /data
WORKDIR /package

RUN yum update -y
RUN yum upgrade -y
RUN yum install python -y
RUN yum install openssl -y
RUN yum install ntpdate -y
RUN yum install net-tools -y
RUN yum install crontabs -y
RUN yum install initscripts -y

WORKDIR /var/spool/cron

ADD ./SniperWebServer_v2.0.1-2-gdeb59a5.tar.gz /package
ADD ./2.0.7-11-g9326005.tar.gz /package

WORKDIR /package/SniperWebServer_v2.0.1-2-gdeb59a5
RUN ./install.sh
WORKDIR /package/2.0.7-11-g9326005
ENV TZ Asia/Seoul
ENV TERM xterm

RUN ./install.sh 8500

EXPOSE 8500
CMD [ "service", "httpd", "restart" ]
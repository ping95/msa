FROM centos:7.4.1708

RUN mkdir /home1
RUN mkdir /data
RUN mkdir /package
RUN mkdir -p /var/spool/cron

RUN yum update -y
RUN yum upgrade -y
RUN yum install python -y
RUN yum install openssl -y
RUN yum install ntpdate -y
RUN yum install net-tools -y
RUN yum install crontabs -y
RUN yum install initscripts -y

# 패키지 복사
ADD ./SniperWebServer_v2.0.1-16-g432b58e.tar.gz /package
ADD ./2.0.7-11-g9326005.tar.gz /package

# 웹서버 설치
WORKDIR /package/SniperWebServer_v2.0.1-16-g432b58e
RUN ./install.sh

# RMS 설치
WORKDIR /package/2.0.7-11-g9326005
ENV TZ Asia/Seoul
ENV TERM xterm
RUN ./install.sh
 
#Volumn 설정
VOLUME /home1/apache/conf
VOLUME /home1/snipre_rms/dbb
VOLUME /home1/snipre_rms/console_cgi
VOLUME /data/snipre_rms

WORKDIR /home1/sniper_rms
CMD ["/home1/apache/bin/httpd", "-D", "FOREGROUND"]
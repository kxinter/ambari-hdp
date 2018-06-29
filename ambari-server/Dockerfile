FROM ambari:base
MAINTAINER kxinter.man 327686635@qq.com
# repo
ARG  hdprepo=192.168.1.3
COPY repo/ambari.repo /etc/yum.repos.d/
COPY repo/HDP.repo /etc/yum.repos.d/
COPY repo/HDP-UTILS.repo /etc/yum.repos.d/
# ambari-server/ambari-agent
RUN yum install -y ambari-server ambari-agent \
  &&  rm -rf /etc/ambari-server/ambari.properties \
  &&  rm -rf /etc/ambari-server/password.dat
COPY ambari-server-conf/ambari.properties /etc/ambari-server/conf/
COPY ambari-server-conf/password.dat /etc/ambari-server/conf/
# ambari mysql connector
RUN mkdir /usr/share/java/
COPY mysql/mysql-connector-java.jar /usr/share/java/
# install mysql
COPY mysql/mysql.tar.gz /var/lib/
RUN cd /var/lib/ \
  &&  tar -zxvf mysql.tar.gz \
  &&  rm -rf mysql.tar.gz \
  &&  yum install -y mariadb-server mariadb
# auto start
RUN systemctl enable mariadb \
  &&  systemctl enable ambari-server
# Ambari UI ports
EXPOSE 8080
# Hdfs ports
#EXPOSE 50010 50020 50070 50075 50090 8020 9000
# Mapred ports
#EXPOSE 19888
#Yarn ports
#EXPOSE 8030 8031 8032 8033 8040 8042 8088
#Other ports
#EXPOSE 49707 2122


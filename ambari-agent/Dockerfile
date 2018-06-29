FROM ambari:base
MAINTAINER kxinter.man 327686635@qq.com
# repo
COPY repo/ambari.repo /etc/yum.repos.d/
COPY repo/HDP.repo /etc/yum.repos.d/
COPY repo/HDP-UTILS.repo /etc/yum.repos.d/
# install ambari-agent
RUN yum install -y ambari-agent \
  && rm -rf /etc/yum.repos.d/HDP* \
  && rm -rf /etc/yum.repos.d/ambari.repo \
  && systemctl enable sshd
# Hdfs ports
EXPOSE 50010 50020 50070 50075 50090 8020 9000
# Mapred ports
EXPOSE 19888
# Yarn ports
EXPOSE 8030 8031 8032 8033 8040 8042 8088
# Other ports
EXPOSE 49707 2122


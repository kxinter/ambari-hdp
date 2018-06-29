# 制作ambar hdp docker容器
此方案开启了镜像systemd命令，在测试中，发现ambar安装hdp集群时会用到systemctl命令，为避免出错，采用此方式
# 参考
https://github.com/sequenceiq/docker-ambari
# 资源下载：
Ambari	http://public-repo-1.hortonworks.com/ambari/centos7/2.x/updates/2.5.1.0/ambari-2.5.1.0-centos7.tar.gz
HDP	http://public-repo-1.hortonworks.com/HDP/centos7/2.x/updates/2.6.1.0/HDP-2.6.1.0-centos7-rpm.tar.gz
HDP-UTILS	http://public-repo-1.hortonworks.com/HDP-UTILS-1.1.0.21/repos/centos7/HDP-UTILS-1.1.0.21-centos7.tar.gz
# 要点：
1、自建network ，启用dockerDNS
docker network create --driver bridge my-net
2、所有容器启动方式必须按照如下方式
   #开启privileged,映射本地路径，开启systemd,使用网络my-net,使DNS生效。（单机方案，多节点根据情况修改）
docker run --name test --network=my-net --privileged=true -d -v /sys/fs/cgroup:/sys/fs/cgroup:ro ambari:agent
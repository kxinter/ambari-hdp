# ����ambar hdp docker����
�˷��������˾���systemd����ڲ����У�����ambar��װhdp��Ⱥʱ���õ�systemctl���Ϊ����������ô˷�ʽ
# �ο�
https://github.com/sequenceiq/docker-ambari
# ��Դ���أ�
Ambari	http://public-repo-1.hortonworks.com/ambari/centos7/2.x/updates/2.5.1.0/ambari-2.5.1.0-centos7.tar.gz
HDP	http://public-repo-1.hortonworks.com/HDP/centos7/2.x/updates/2.6.1.0/HDP-2.6.1.0-centos7-rpm.tar.gz
HDP-UTILS	http://public-repo-1.hortonworks.com/HDP-UTILS-1.1.0.21/repos/centos7/HDP-UTILS-1.1.0.21-centos7.tar.gz
# Ҫ�㣺
1���Խ�network ������dockerDNS
docker network create --driver bridge my-net
2����������������ʽ���밴�����·�ʽ
   #����privileged,ӳ�䱾��·��������systemd,ʹ������my-net,ʹDNS��Ч����������������ڵ��������޸ģ�
docker run --name test --network=my-net --privileged=true -d -v /sys/fs/cgroup:/sys/fs/cgroup:ro ambari:agent
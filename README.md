# Consul Helm Chart

This is used for consul cluster internal k8s cluster, with both consul server internal k8s cluster and consul client


# node outside k8s集群的加入命令：
sudo docker run -d --net=host -e 'CONSUL_ALLOW_PRIVILEGED_PORTS=1' -h 10-37-65-97 \
  --name consul_client -v /home/ec2-user/consulinstall/shellinstalldocker/config:/home/consul/.kube/config consul:1.2.3 agent -dns-port=53 \
  -bind=${IP} -client ${CLIENT_IP} -retry-join 'provider=k8s  label_selector="app=consul,component=server"'  \
  -recursor 8.8.8.8 -recursor 8.8.4.4
  
  

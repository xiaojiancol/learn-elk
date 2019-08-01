
### docker 仓库配置

wget https://artifacts.elastic.co/downloads/logstash/logstash-6.8.2.zip
logstash -f log stash.conf

### 集群运行

多实例，多节点的运行

bin/elasticsearch -E node.name=node1 -E cluster.name=xxx -E path.data=xxx -d

## FAQ  

- elastic 需要 单独用户安装  
- elastic 初识的配置需要  

http://192.168.1.200:5601  
http://192.168.1.200:9000  
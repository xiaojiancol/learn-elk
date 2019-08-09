# Introduction

目前这些资源是参照7.x的版本开发的。  

引入ELK，目标不是降低日志存储空间，相反一定会增加日志存储空间。  
引入ELK的目标是便于日志分析（连管理功能都没有），继而产生各种附加值、衍生品，比如故障通知、故障分析、性能分析、性能估算和预警。  

## 目录

Elastic Stack

### Getting started
#### Getting started with the Elastic Stack
#### Running the Elastic Stack on Docker
#### Running the Elastic Stack on Kubernetes
### Stack Overview [7.3] — other versions
#### Introduction
#### Securing the Elastic Stack
#### Monitoring the Elastic Stack
#### Alerting on cluster and index events
#### Data frame transforms
#### Machine learning anomaly detection
#### Machine learning data frame analytics
#### Cross-cluster replication
#### License management
### Elastic Common Schema (ECS) Reference [1.0] — other versions
### Azure Marketplace and Resource Manager (ARM) template [7.2] — other versions
### Elastic Stack and Google Cloud’s Anthos

Elasticsearch: Store, Search, and Analyze

### Elasticsearch Reference [7.3] — other versions
### Elasticsearch Resiliency Status
### Painless Scripting Language [7.3] — other versions
### Plugins and Integrations [7.3] — other versions
### Elasticsearch Clients
### Elasticsearch for Apache Hadoop and Spark [7.3] — other versions
### Curator Index Management [5.7] — other versions

Cloud: Provision, Manage and Monitor the Elastic Stack

### Elasticsearch Service - Hosted Elasticsearch and Kibana [release-ms-24] — other versions
### Elasticsearch Add-On for Heroku - Hosted Elasticsearch and Kibana for Heroku Users
### Elastic Cloud Enterprise - Elastic Cloud on your Infrastructure [2.3] — other versions
### Elastic Cloud on Kubernetes [0.9] — other versions

Kibana: Explore, Visualize, and Share

### Kibana Reference [7.3] — other versions

Logstash: Collect, Enrich, and Transport

### Logstash Reference [7.3] — other versions
### Logstash Versioned Plugin Reference

Beats: Collect, Parse, and Ship

### Beats Platform Reference [7.3] — other versions
### Beats Developer Guide [master] — other versions
### Packetbeat Reference [7.3] — other versions
### Filebeat Reference [7.3] — other versions
### Winlogbeat Reference [7.3] — other versions
### Metricbeat Reference [7.3] — other versions
### Heartbeat Reference [7.3] — other versions
### Auditbeat Reference [7.3] — other versions
### Functionbeat Reference [7.3] — other versions
### Journalbeat Reference [7.3] — other versions
### Legacy Topbeat Reference [1.3] — other versions

## 参考

https://www.elastic.co/guide/en/logstash/current/index.html  
https://www.elastic.co/cn/products  
https://www.elastic.co/start  

### FAQ

1. 如何查看Packagebeat
2. 汉化问题  
  https://github.com/elastic/kibana/issues/6515 
  https://github.com/anbai-inc/Kibana_Hanization  
  汉化不成功
3. 慢查询按耗时长度排序
4. SQL去重
5. Fielddata is disabled on text fields by default. Set fielddata=true on [your_field_name]  
  https://www.jianshu.com/p/2d86eafc3e94  
6. unicode 编码
  https://www.jianshu.com/p/2d86eafc3e94  
7. 
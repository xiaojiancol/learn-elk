
## Configuring Monitoring in Kibanaedit

X-Pack monitoring gives you insight into the operation of your Elastic Stack. For more information, see X-Pack monitoring and Monitoring the Elastic Stack.

X-Pack监控使您可以深入了解弹性堆栈的操作。 有关更多信息，请参阅X-Pack监视和监视弹性堆栈。

1. To monitor Kibana:
要监控Kibana：  
    a. Verify that the xpack.monitoring.collection.enabled setting is true on the production cluster. If that setting is false, which is the default value, the collection of monitoring data is disabled in Elasticsearch and data is ignored from all other sources. For more information, see Monitoring Settings in Elasticsearch.  
    确认生产群集上的xpack.monitoring.collection.enabled设置是否为true。 如果该设置为false（默认值），则在Elasticsearch中禁用监视数据集合，并从所有其他源中忽略数据。 有关更多信息，请参阅Elasticsearch中的监控设置。  

    b. Verify that xpack.monitoring.enabled and xpack.monitoring.kibana.collection.enabled are set to true, which are the default values. For more information, see Monitoring Settings.  
    验证xpack.monitoring.enabled和xpack.monitoring.kibana.collection.enabled是否设置为true，这是默认值。 有关更多信息，请参阅监控设置。 

    c. Identify where to send monitoring data. Kibana automatically sends metrics to the Elasticsearch cluster specified in the elasticsearch.url setting in the kibana.yml file. This property has a default value of http://localhost:9200. This cluster is often referred to as the production cluster.  
    确定监控数据的发送位置。 Kibana会自动将指标发送到kibana.yml文件中elasticsearch.url设置中指定的Elasticsearch集群。 此属性的默认值为http：// localhost：9200。 此群集通常称为生产群集。

> If X-Pack security is enabled on the production cluster, use an HTTPS URL such as https://<your_production_cluster>:9200 in this setting.

2. To visualize monitoring data:  
  要可视化监控数据：

    a. Verify that xpack.monitoring.ui.enabled is set to true, which is the default value. For more information, see Monitoring Settings.  
    验证xpack.monitoring.ui.enabled是否设置为true，这是默认值。 有关更多信息，请参阅监控设置。  
    
    b. Identify where to retrieve monitoring data from. If you want to use a separate monitoring cluster, set xpack.monitoring.elasticsearch.url in the kibana.yml file. Otherwise, the monitoring data is stored in the production cluster.  
    确定从哪里检索监控数据。 如果要使用单独的监视集群，请在kibana.yml文件中设置xpack.monitoring.elasticsearch.url。 否则，监视数据将存储在生产群集中。

    To learn more about typical monitoring architectures with separate production and monitoring clusters, see How Monitoring Works.  
    要了解有关具有单独生产和监视集群的典型监视体系结构的更多信息，请参阅监视工作原理

> If X-Pack security is enabled on the monitoring cluster, use an HTTPS URL such as https://<your_monitoring_cluster>:9200 in this setting.  如果在监视群集上启用了X-Pack安全性，请在此设置中使用HTTPS URL，例如https：// <your_monitoring_cluster>：9200

3. If X-Pack security is enabled on the production cluster:  
......

4. If X-Pack security is enabled on the monitoring cluster:  
......

5. Restart Kibana.

6. If X-Pack security is enabled on your Kibana server:  
......

### Monitoring Settings in Kibana

By default, the Monitoring application is enabled, but data collection is disabled. When you first start Kibana monitoring, you will be prompted to enable data collection.  
默认情况下，启用监控应用程序，但禁用数据收集。 首次启动Kibana监控时，系统将提示您启用数据收集。

You can adjust how monitoring data is collected from Kibana and displayed in Kibana by configuring settings in the kibana.yml file. There are also xpack.monitoring.elasticsearch.* settings, which support the same values as Kibana configuration settings.  
您可以通过配置kibana.yml文件中的设置来调整从Kibana收集监控数据并在Kibana中显示的方式。 还有xpack.monitoring.elasticsearch.*设置，它们支持与Kibana配置设置相同的值。

To control how data is collected from your Elasticsearch nodes, you configure xpack.monitoring.collection settings in elasticsearch.yml. To control how monitoring data is collected from Logstash, you configure xpack.monitoring settings in logstash.yml.  
要控制从Elasticsearch节点收集数据的方式，请在elasticsearch.yml中配置xpack.monitoring.collection设置。 要控制从Logstash收集监视数据的方式，请在logstash.yml中配置xpack.monitoring设置。

For more information, see Monitoring the Elastic Stack.  
有关更多信息，请参阅监视弹性堆栈。

#### General Monitoring ... 剩下全是关于xpack的介绍
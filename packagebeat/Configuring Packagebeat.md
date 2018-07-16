Before modifying configuration settings, make sure you’ve completed the [configuration](https://www.elastic.co/guide/en/beats/packetbeat/current/packetbeat-configuration.html) steps in the Getting Started. This section describes some common use cases for changing configuration options.
在修改配置设置之前，请确保已完成“入门”中的配置步骤。 本节介绍了更改配置选项的一些常见用例。

To configure Packetbeat, you edit the configuration file. For rpm and deb, you’ll find the configuration file at /etc/packetbeat/packetbeat.yml. There’s also a full example configuration file at /etc/packetbeat/packetbeat.reference.yml that shows all non-deprecated options. For mac and win, look in the archive that you extracted.
要配置Packetbeat，请编辑配置文件。 对于rpm和deb，您可以在/etc/packetbeat/packetbeat.yml找到配置文件。 /etc/packetbeat/packetbeat.reference.yml上还有一个完整的示例配置文件，显示了所有未弃用的选项。 对于mac和win，请查看您提取的存档。

The Packetbeat configuration file uses [YAML](http://yaml.org/) for its syntax. See the [Config File Format](http://www.elastic.co/guide/en/beats/libbeat/6.3/config-file-format.html) section of the Beats Platform Reference for more about the structure of the config file.
Packetbeat配置文件使用YAML作为其语法。 有关配置文件结构的更多信息，请参阅Beats Platform Reference的Config File Format部分。

The following topics describe how to configure Packetbeat:
以下主题描述了如何配置Packetbeat：

- Set traffic capturing options
- Set up flows to monitor network traffic
- Specify which transaction protocols to monitor
- Specify which processes to monitor
- Specify general settings
- Configure the internal queue
- Configure the output
- Specify SSL settings
- Filter and enhance the exported data
- Parse data by using ingest node
- Export GeoIP Information
- Set up project paths
- Set up the Kibana endpoint
- Load the Kibana dashboards
- Load the Elasticsearch index template
- Configure logging
- Use environment variables in the configuration
- YAML tips and gotchas
- packetbeat.reference.yml
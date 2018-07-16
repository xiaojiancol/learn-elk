https://www.elastic.co/guide/en/beats/packetbeat/current/packetbeat-getting-started.html

# Getting started with Packetbeat
The best way to understand the value of a network packet analytics system like Packetbeat is to try it on your own traffic.  
了解Packetbeat等网络数据包分析系统价值的最佳方法是根据自己的流量进行尝试.

To get started with your own Packetbeat setup, install and configure these related products:
安装Packagebeat之前你需要安装这些相关的产品。
- Elasticsearch for storing and indexing the data.
- Kibana for the UI.
- Logstash (optional) for parsing and enhancing the data.

See [Getting started with the Elastic](https://www.elastic.co/guide/en/elastic-stack-overview/6.3/get-started-elastic-stack.html) Stack for more information.

After installing the Elastic Stack, read the following topics to learn how to install, configure, and run Packetbeat:
安装Elastic Stack之后，阅读以下topic学习如何安装、配置、运行Packagebeat

- Step 1: Install Packetbeat
- Step 2: Configure Packetbeat
- Step 3: Load the index template in Elasticsearch
- Step 4: Set up the Kibana dashboards
- Step 5: Start Packetbeat
- Step 6: View the sample Kibana dashboards
- Repositories for APT and YUM

## Step 1: Install Packetbeat
**Before you begin**: If you haven’t installed the Elastic Stack, do that now. See [Getting started with the Elastic Stack](https://www.elastic.co/guide/en/elastic-stack-overview/6.3/get-started-elastic-stack.html).

To download and install Packetbeat, use the commands that work with your system (deb for Debian/Ubuntu, rpm for Redhat/Centos/Fedora, mac for OS X, docker for any Docker platform, and win for Windows).

> If you use Apt or Yum, you can [install Packetbeat from our repositories]() to update to the newest version more easily.
> See our [download page]() for other installation options, such as 32-bit images.

deb:
>...

rpm:
>...

docker:
>...

mac:
>...

win:
1. Download and install WinPcap from this [page](http://www.winpcap.org/install/default.htm). WinPcap is a library that uses a driver to enable packet capturing.
2. Download the Packetbeat Windows zip file from the [downloads page](https://www.elastic.co/downloads/beats/packetbeat).
3. Extract the contents of the zip file into C:\Program Files.
4. Rename the `packetbeat-<version>-windows` directory to Packetbeat.
5. Open a PowerShell prompt as an Administrator (right-click the PowerShell icon and select **Run As Administrator**).
6. From the PowerShell prompt, run the following commands to install Packetbeat as a Windows service:
>PS > cd 'C:\Program Files\Packetbeat'  
>PS C:\Program Files\Packetbeat> .\install-service-packetbeat.ps1

>If script execution is disabled on your system, you need to set the execution policy for the current session to allow the script to run. For example: PowerShell.exe -ExecutionPolicy UnRestricted -File .\install-service-packetbeat.ps1.

Before starting Packetbeat, you should look at the configuration options in the configuration file, for example `C:\Program Files\Packetbeat\packetbeat.yml` or `/etc/packetbeat/packetbeat.yml`. For more information about these options, see [Configuring Packetbeat](https://www.elastic.co/guide/en/beats/packetbeat/current/configuring-howto-packetbeat.html).

## Step 2: configure Packetbeat

To configure Packetbeat, you edit the configuration file. For rpm and deb, you’ll find the configuration file at /etc/packetbeat/packetbeat.yml. Under Docker, it’s located at /usr/share/packetbeat/packetbeat.yml. For mac and win, look in the archive that you just extracted. There’s also a full example configuration file called packetbeat.reference.yml that shows all non-deprecated options.

See the [Config File Format]() section of the Beats Platform Reference for more about the structure of the config file.

To configure Packetbeat:


## Step 3: Load the index template in Elasticsearch

In Elasticsearch, [index templates]() are used to define settings and mappings that determine how fields should be analyzed.

The recommended index template file for Packetbeat is installed by the Packetbeat packages. If you accept the default configuration in the packetbeat.yml config file, Packetbeat loads the template automatically after successfully connecting to Elasticsearch. If the template already exists, it’s not overwritten unless you configure Packetbeat to do so.
Packetbeat的推荐索引模板文件由Packetbeat软件包安装。 如果您接受packetbeat.yml配置文件中的默认配置，则Packetbeat会在成功连接到Elasticsearch后自动加载模板。 如果模板已存在，则除非您将Packetbeat配置为执行此操作，否则不会覆盖该模板。 

You can disable automatic template loading, or load your own template, by configuring template loading options in the Packetbeat configuration file.
您可以通过在Packetbeat配置文件中配置模板加载选项来禁用自动模板加载或加载您自己的模板。

You can also set options to change the name of the index and index template.
您还可以设置选项以更改索引和索引模板的名称。

>A connection to Elasticsearch is required to load the index template. If the output is Logstash, you must [load the template manually](https://www.elastic.co/guide/en/beats/packetbeat/current/packetbeat-template.html#load-template-manually).

For more information, see:

- [Configure template loading](https://www.elastic.co/guide/en/beats/packetbeat/current/packetbeat-template.html#load-template-auto)
- [Load the template manually](https://www.elastic.co/guide/en/beats/packetbeat/current/packetbeat-template.html#load-template-manually) - required for Logstash output

......

## Step 4: Set up the Kibana dashboards  

## Step 5: Start Packetbeat  

## Step 6: View the sample Kibana dashboards   

## Repositories for APT and YUM  
















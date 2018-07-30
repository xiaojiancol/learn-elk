# Loading Sample Data
This tutorial requires three data sets:

- The complete works of William Shakespeare, suitably parsed into fields. Download shakespeare.json.  
威廉莎士比亚的全部作品，适当地解析成领域。 下载shakespeare.json。  

- A set of fictitious accounts with randomly generated data. Download accounts.zip.  
一组带有随机生成数据的虚构帐户。 下载accounts.zip。

- A set of randomly generated log files. Download logs.jsonl.gz.
一组随机生成的日志文件。 下载logs.jsonl.gz。

Two of the data sets are compressed. To extract the files, use these commands:  
其中两个数据集是压缩的。 要提取文件，请使用以下命令：  

```{}
unzip accounts.zip
gunzip logs.jsonl.gz
```

The Shakespeare data set has this structure:  
...

The accounts data set is structured as follows:  
...

The logs data set has dozens of different fields. Here are the notable fields for this tutorial:
...

Before you load the Shakespeare and logs data sets, you must set up mappings for the fields. Mappings divide the documents in the index into logical groups and specify the characteristics of the fields. These characteristics include the searchability of the field and whether it’s tokenized, or broken up into separate words.

在加载莎士比亚和日志数据集之前，必须为字段设置映射。 映射将索引中的文档划分为逻辑组，并指定字段的特征。 这些特征包括字段的可搜索性以及它是否被标记化，或者分解为单独的单词。

In Kibana Dev Tools > Console, set up a mapping for the Shakespeare data set:


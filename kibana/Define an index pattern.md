
# Defining Your Index Patternsedit

Index patterns tell Kibana which Elasticsearch indices you want to explore. An index pattern can match the name of a single index, or include a wildcard (*) to match multiple indices.

索引模式告诉Kibana您想要探索哪些Elasticsearch索引。 索引模式可以匹配单个索引的名称，或者包含通配符（*）以匹配多个索引。

For example, Logstash typically creates a series of indices in the format logstash-YYYY.MMM.DD. To explore all of the log data from May 2018, you could specify the index pattern logstash-2018.05*.

例如，Logstash通常以logstash-YYYY.MMM.DD格式创建一系列索引。 要浏览2018年5月的所有日志数据，您可以指定索引模式logstash-2018.05 *。

Create patterns for the Shakespeare data set, which has an index named shakespeare, and the accounts data set, which has an index named bank. These data sets don’t contain time-series data.

为莎士比亚数据集创建模式，该数据集具有名为shakespeare的索引，以及具有名为bank的索引的帐户数据集。 这些数据集不包含时间序列数据。

1. In Kibana, open Management, and then click Index Patterns.
2. If this is your first index pattern, the Create index pattern page opens automatically. Otherwise, click Create index pattern in the upper left.
3. Enter shakes* in the Index pattern field.
![](https://www.elastic.co/guide/en/kibana/current/images/tutorial-pattern-1.png)
4. Click Next step.  
5. In Configure settings, click Create index pattern. For this pattern, you don’t need to configure any settings.
6. Define a second index pattern named ba* You don’t need to configure any settings for this pattern.

Now create an index pattern for the Logstash data set. This data set contains time-series data.

1. Define an index pattern named logstash*.
2. Click Next step.
3. In Configure settings, select @timestamp in the Time Filter field name dropdown menu.
4. Click Create index pattern.


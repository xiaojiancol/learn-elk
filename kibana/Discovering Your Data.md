# Discovering Your Dataedit

Using the Discover application, you can enter an Elasticsearch query to search your data and filter the results.
使用Discover应用程序，您可以输入Elasticsearch查询来搜索数据并过滤结果。

1. Open Discover. The shakes* pattern is the current index pattern.
2. Click the caret to the right of shakes*, and select ba*.
3. In the search field, enter the following string:
> account_number:<100 AND balance:>47500

The search returns all account numbers between zero and 99 with balances in excess of 47,500. It returns results for account numbers 8, 32, 78, 85, and 97.

搜索返回0到99之间的所有帐号，余额超过47,500。 它返回帐号8,32,78,85和97的结果。

By default, all fields are shown for each matching document. To choose which fields to display, hover the mouse over the the list of Available Fields and then click add next to each field you want include.

默认情况下，会为每个匹配的文档显示所有字段。 要选择要显示的字段，请将鼠标悬停在“可用字段”列表上，然后单击要包括的每个字段旁边的“添加”。

For example, if you add the account_number field, the display changes to a list of five account numbers.

例如，如果添加account_number字段，则显示将更改为包含五个帐号的列表。


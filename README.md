## 站点公开信息搜索工具
### 功能说明
通过Google和Baidu搜索引擎自带的高级搜索功能检索特定域名的索引信息，可通过自定义的高级搜索语句进行检索，并输出到特定文件中。
当只通过site关键词检索域名时，将输出两种搜索引擎检索子域名情况。

### 实现说明
* Google搜索：

就是爬虫而已，但因为Google的机器人检测机制，每次请求Google页面期间需要随机等待至少15s以上，否则容易被识别为机器人。

* Baidu搜索：

Baidu的搜索结果URL是经过加密的，通过二次请求的方式可获得真实的URL，因此采用多线程请求。但Baidu对或搜索的支持并不是很好，高级搜索语句的或搜索会显示无结果，因此每次搜索只能设置一次关联关键词，例如："inurl:setup site:baidu.com'，而"inurl:setup inurl:install site:baidu.com'会显示无搜索结果，即便用|或OR。

### 注意事项
因为Google搜索的原因，执行环境必须能够翻墙。

### 使用说明
```
usage: sitedork.py [-h] [-l limit] -d domain

Information Dork tool for searching domains,files and emails.

optional arguments:

	-h, --help	show this help message and exit

	-l limit, --limit limit		results of searching limit(default:1000)

	-d domain, --domain domain 	domain name for searching
```

### 搜索条件定义

为了方便搜索条件的扩展或自定义，代码中并未对已有搜索引擎进行强关联以及进一步的优化。所以如果你想的话，可以对搜索条件进行自定义，但是要注意site语法必须在行首，否则在判断子域名时会失效。

### 还可以做更多

* 将搜索条件放置在配置文件中进行读取
* 结合数据库存储可配置的搜索条件以及结果
* 通过自定义的搜索条件实现简单的舆情监控

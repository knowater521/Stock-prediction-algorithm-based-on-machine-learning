##使用机器学习算法进行量化分析

###项目很乱！！！
###项目很乱！！！
###项目很乱！！！

不多说废话，直接说明项目，关键字：**量化投资、机器学习、股票交易**。该项目包括多个部分
1. 数据收集
2. 基本面分析
3. 技术面分析
4. 消息面分析
5. 回测系统


**1. 数据收集**
【文件夹：get_data】
该部分用来获取原始的数据，主要用于基本面和技术面分析，数据来源是通过python的tushare库，tushare是一个成熟的开源的金融信息数据接口[tushare](http://tushare.org)，里面提供了多个不同的函数来获取各种不同的表格数据，存储于.csv文件中。
【文件夹：news】
cctv.py是一个爬虫，爬取CCTV新闻联播的新闻内容，并筛选关键词。TextSpider.py也是一个爬虫，爬取CCTV财经新闻内容。这两部分主要用于消息面分析中。

**2. 基本面分析**
【文件夹：基本面传统算法】
a-f.py是基本面分析中使用ROE算法进行分析的各个步骤，data.csv是这个过程中的临时数据，以及存在的各个年度的财务报表。
在基本面分析中使用了传统的ROE因子选股策略，机器学习算法为朴素贝叶斯算法。选用2016年-2019年沪深300成分股的前三季度的财务报表进行分析，通过不同的策略进行选股，并分析投资组合收益率。
在这里的传统ROE算法为：
1. 2016-2018三年的ROE值均大于10%
2. 2019年前三季度的ROE均上升，没有下跌
3. 满足以上条件的ROE值前十的股票

回测时期为：2019年10月28号-2019年11月8号

**3. 技术面分析**
【文件夹：个股预测】
在这里面，有多种个股预测的算法，其中里面的multi-thread文件夹是用来进行单日拟合的，进行区分以实现多线程运行。
【文件夹：技术面传统算法】
在这个文件夹中，主要有各种传统的算法，主要为移动平均算法、相对强弱因子，顺带需要分析的数据。
【文件夹：技术面机器学习算法】
技术面分析中使用到的是机器学习算法为：
1.Auto-ARIMA算法
2.LSTM算法
3.Prophet算法
4.SVM算法
其中，SVM算法是用于定性分析，在测试中SVM的成功率非常高。其他的各种算法用于定量分析，在定量分析中，又分为单次回归和单日回归，其中各种算法的优势比较为：

| 机器学习算法        | 单次拟合效果   |  单日拟合效果  |  算法效率 |
| --------   | -----:  | :----:  |  |
| Auto-ARIMA      | 较差   |   很好     |非常慢|
| Prophet      |   较差   |   较好   |  较慢|
| LSTM        |    较好    |  较好  |快|

**4. 消息面分析**
广泛来说，消息面分析的数据是海量的，根本分析不完。在这里是选用了CCTV新闻联播节目中的近几个月的消息，使用jieba分词库和snownlp情感分析库进行分析，提取关键词，获得需要关注的模块信息。
【文件夹：news】
在这里面的各种data.txt文件是各种新闻信息，snownlp.py文件用来进行情感分析，cctv.txt是进行关键词提取之后的新闻标题。
-
*然而，经历了2020年年初的新冠肺炎疫情我们可以认定，市场的总体走势其实是由宏观经济情况和其他非经济因素所影响的，这里面涉及到消息面分析，而对于个股分析中，才涉及到基本面和技术面分析*

**5. 回测系统**
【文件夹：sz50】
回测系统是自己搭建的，用于进行回测，但是比较简单，没有涉及到交易费用，只是实现了股票的买入卖出和收益率的计算，对于各种因素指标的实现需要之后再进行实现，以及数据可视化部分，并没有类似于聚宽平台<https://www.joinquant.com/>这样的一个比较完整的回测平台。
在这里主要是对技术面算法的数据进行回测，使用的数据集市上证50指数的成分股，可以获得回测的收益率。
【文件夹：prediction】
这个文件夹里面包含的是进行回测的数据，多种机器学习的算法进行测试。

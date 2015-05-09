# 互联网数据挖掘

万小军 http://www.icst.pku.edu.cn/lcwm

<!-- MarkdownTOC -->

- 互联网挖掘概述
- 文本信息检索
- 数据挖掘概述与关联规则挖掘
    - 数据挖掘流程
    - 数据挖掘任务
- 分类
    - 基于规则的分类
    - 基于统计的分类
    - 文本统计分类流程
    - 文本分类-特征向量表示
    - 文本分类-特征选择
    - 朴素贝叶斯分类
    - Rocchio 分类方法
    - K 近邻分类方法
    - 支持向量机 Support Vector Machine
    - 分类结果评估
    - 如何应用于实际
- 聚类
    - 层次式聚类
    - K 均值(K-means)聚类
    - Buckshot 算法
    - 增量式单遍聚类(Single-Pass)
    - 基于图分割的聚类
    - 基于密度峰值的聚类(Science)
    - 半监督聚类
    - 聚类结果评估
    - 聚类算法的选择
    - 半监督聚类
    - 检索结果聚类
- 关联规则挖掘：定义
- 摘要
- 回归
- 偏差/异常检测
- 数据挖掘工具
- 数据挖掘的挑战

<!-- /MarkdownTOC -->

## 互联网挖掘概述

+ Web 挖掘
    + 由 Etzioni(1996) 提出
    + 使用数据挖掘的技术自动从 Web文档/服务发现和提取信息和知识，包括隐含的模式和关系等
+ 相关技术
    + 信息检索
    + 互联网
    + 数据库
    + 机器学习
    + 自然语言处理
    + 数据挖掘
+ 相关学术会议
    + Web 搜索: SIGIR, WWW, CIKM, WSDM
    + 数据挖掘: KDD, ICDM
    + 自然语言处理: ACL, EMNLP
    + 多媒体检索: ACM, MM
+ 应用
    + 垂直搜索
    + 个性化推荐
    + 智能问答
    + 机器翻译
    + 舆情监测
    + 情报与反恐
    + 预测

## 文本信息检索

+ 两个核心问题

## 数据挖掘概述与关联规则挖掘

数据挖掘从多学科领域发展而来：Statistics/AI, Machine Learning, Pattern Recognition, Database systems

### 数据挖掘流程

**Data** -Selection-> **Target data** -Preprocessing-> **Preprocessed data** -Transformation-> **Transformed data** -Data mining-> **Patterns** -Interpretation/evaluatoin-> **Knowledge**

### 数据挖掘任务

+ 预测型(Prediction Methods): 基于一些变量预测其他变量的未知值或未来值
    + 分类 Classification
    + 回归 Regression
    + 偏差检测 Deviation Detection
+ 描述型(Description Methods): 发现描述数据的人们可解释的模式
    + 聚类 Clustering
    + 关联规则挖掘 Association Rule Discovery
    + 摘要 Summarization

## 分类

将数据划分到已知类别。分类器的构建基于有监督学习(标注数据:训练集)

+ 给定一个样例集合(训练集)
    + 每个样例包含一个属性集合，其中一个属性是类标记/类号
+ 基于训练集构建一个模型，该模型将类标记属性看作是其它属性值的一个函数
+ 目标：对心的样例尽可能准确地赋予标记
    + 基于一个测试集来评估模型的准确性

Training Set -> Learn Classifier -> Model <- Test set

+ 二类分类：正、负
+ 多类分类：多类(>=3)

二类分类是分类问题的最基本形式，多类分类问题可通过转化为二类分类问题加以解决。

+ One vs. One
    + 对于 K 类分类需要 K(K-1)/2 个二类分类器
    + 测试分类时采用投票方式确定类别
    + E.g. Labels: a, b, c
    + 分类器: a vs b, b vs c, a vs c
+ One vs. All(Rest):
    + 对于 K 类分类需要 K 个二类分类器
    + 测试分类时取返回最大值的类别
    + E.g. Labels: a, b, c
    + 分类器: a vs (b, c), b vs (a, c), c vs (a, b)

层次式分类，类别构成层次式结构(树状)。中图法、ODP目录。

+ 应用
    + 新闻分类
    + 广告页面判别
    + 垃圾邮件过滤
    + 垃圾短信过滤
    + 博客风格判断
    + 评论情感分析

### 基于规则的分类

人工/专家制定分类规则，使用布尔操作符(AND, OR, NOT)，可将规则组织成决策树，节点代表规则，叶节点代表类别

+ 优势
    + 透明，易于理解，易于修改
+ 劣势
    + 复杂，耗时
    + 主要依赖人工/专家的智能，而非系统/机器智能
    + 不易拓展
    + 绝对的类别划分，无置信度

### 基于统计的分类

+ 优势
    + 可以输出置信概率、允许阈值控制、可扩展
+ 劣势
    + 需要已标注好的训练数据
+ 典型方法
    + 朴素贝叶斯
    + Rocchio
    + K 近邻
    + 支持向量机

### 文本统计分类流程

+ 预处理
    + Tokenization
    + Filtering
    + Stemming
+ 特征计算
    + tf
    + Log(tf+1)
    + tfidf
+ 特征选择
    + MI
    + Chi-Square
    + Information Gain
+ 分类学习
    + SVM
    + Rocchio
    + Naive Bayes
+ 结果评估
    + Recall
    + F-Measure
    + Precision

### 文本分类-特征向量表示

+ 文本表示为特征向量
    + 词语(term): 基本单元
    + 权重 TF * IDF
        + TF: 词频
        + IDF: log(N/DF), N 为文档总数量，DF 为包含该词语的文档数量

### 文本分类-特征选择

+ 好处
    + 减少特征维数，改善效果
    + 防止过拟合，增强模型的泛化能力
    + 提高学习效率
    + 提高模型的可解释性
+ 方法，从原有特征集合中找出一个更加有效的子集
    + Document Frequency 文档频率
        + 词语的 DF 小于某个阈值去掉(太小，没有代表性)
        + 词语的 DF 大于某个阈值也去掉(太多，没有区分度)
    + Mutual Information 互信息
        + MI 越大词语 t 和 c 共现程度越大
    + Information Gain 信息增益
        + 词语 t 为整个分类所能提供的信息量(不考虑任何特征的熵和考虑该特征后的熵的差值)
    + Information Ratio
    + Chi Squrae
    + Odd Ratio

### 朴素贝叶斯分类

+ 基于概率理论的学习和分类方法
+ 贝叶斯理论充当重要角色
+ 分类是根据给定样本描述的可能的类别基础上产生的后验概率分布
    + 基于贝叶斯理论来计算后验概率
+ 分类原理：最大后验估计 MAP(maximum posteriori)

### Rocchio 分类方法

+ 使用中心向量(centroid vector)表示一个类别
    + 中心向量为某个类别下所有文档向量的平均向量
    + 基于训练集计算
+ 对于新文档，计算该文档与每个类别的中心向量的距离/相似度
    + 基于余弦测度
+ 确定其类别为距离最小/相似性最大的类别
+ 优势: 训练快速，模型很小，快速分类
+ 劣势: 类别数量增加时准确率降低

### K 近邻分类方法

+ 与 Rocchio 方法类似
+ 检查新文档的 k 个近邻向量，利用这些近邻向量的类别来确定该文档的类别
    + K 通过实验确定
    + “近邻” 通过相似度/距离测度来定义
+ 1 近邻分类方法
    + 将新文档划分到与其最相近的文档样例所属的类别
+ K 近邻分类方法
    + 基于投票机制，将新文档划分到 k 个近邻文档中多数文档所属的类别
    + 进一步，基于加权投票机制，根据近邻文档的相近程度，赋予每个近邻文档一定的权重
+ 优势
    + 不需要训练阶段
    + 类别数量增加也具有良好的扩展性
+ 劣势
    + 训练数据很大时模型很大
    + 需要大量内存
    + 性能较慢

### 支持向量机 Support Vector Machine

+ 对于二类分类，该方法在向量空间中找出一个决策超平面(分类函数 f(x) = wx + b)，对属于两个类别的文档向量进行有效粉绿
    + 通常有很多可能的分割超平面
    + 找到最好的一个超平面: 最大间隔准则
        + 使得属于不同类别的数据点间隔最大
    + 间隔区边缘上的向量称为支撑向量
+ 实际上要求解一个带约束的二次规划(quadratic programming, QP)问题
+ 训练结果
    + 支撑向量
+ 分类
    + 计算新文档向量与支撑向量的距离
+ 常用工具
    + SVMLight
    + LIBSVM
+ 优势
    + 只有支撑向量用来对新文档分类
    + 模型小
    + 一般不会过拟合
+ 劣势
    + 训练过程非常复杂: 优化问题

### 分类结果评估

+ 对每个分类都可以计算出 precision, recall, F-measure
    + 一般侧重正例的结果
+ 总体评价: 精度(Accuracy) = 正确分类的样本数量 / 总样本数量

### 如何应用于实际

+ 大多数应用都是直接采用已有的分类算法与工具
    + 不需要开发新的
+ 关键在于特征工程
    + 针对特定应用问题寻找合理、有效的特征集
+ 一般需要调节分类算法与工具的多个参数
    + 比如 KNN 中的 K，SVM 中的 C 参数等

## 聚类

+ 给定一个数据点集合，每个数据点具有一组属性，数据点之间能进行相似度度量，聚类目标为找到若干类簇：
    + 同一类簇中的数据点相似
    + 不同类簇中的数据点不相似
+ 无监督学习
    + 没有标注数据
    + 类簇未知
+ 相似度度量准则
    + 欧氏距离(L2 norm)
    + 余弦准则
    + L1 范式(L1 norm)
+ 聚类算法
    + K-Means 聚类
    + 层次式聚类(Hierarchical clustering)
    + 增量式单遍聚类
    + 基于图分割的聚类
    + 基于密度峰值的聚类

应用：文档聚类

+ 目标：发现文档类簇，同一类簇中文档相似(基于重要词语)
+ 方法：识别每篇文档中的重要词语，基于文档相似性进行聚类

### 层次式聚类

+ 自底向上的凝聚式聚类(Agglomerative clustering)
    + 初始每个文档自成一个类簇
    + 每次合并最相似/距离最近的两个类簇，形成一个新类簇，循环执行，直到满足终止条件
        + 终止条件为类簇数量或者相似度阈值
    + 结果为树形图
+ 不同的计算类簇间距离/相似性的方法
    + 最小距离(single link)
    + 最大距离(complete link)
    + 平均距离(group average)
+ 自顶向下的划分式聚类(Divisive clustering)
    + 初始只有一个类簇，包括所有文档
    + 每次从当前类簇中选择最大(或最不合理)的一个类簇，将其分割成两个(或多个)新的类簇，循环执行，直到满足终止条件
        + 类簇分割方法可以采用其他聚类方法，比如 K 均值算法等

### K 均值(K-means)聚类

+ 一种基于划分的聚类算法
+ 算法将文档集划分到 k 个类簇中
    + 每个类簇有一个类簇中心，称为 centroid
    + 可基于该类簇文档向量的平均向量计算
+ K 由用户指定

### Buckshot 算法

结合 K-means 与凝聚式聚类

+ 从原始 n 个数据点中随机取 √n 个数据点
+ 针对这些样本数据点上运行凝聚式聚类
+ 使用凝聚式聚类结果作为初始种子点
+ 在元数据上基于初始种子点运行 K-means

改善了种子点的选择

### 增量式单遍聚类(Single-Pass)

+ 增量式聚类，适合于高效处理动态文本数据流
+ 将新文档与已有类簇逐一对比，如果与某个类簇的相似度值大于设定的阈值，那么将该文档归并到相应类簇中，否则基于该文档形成一个新的类簇
    + 数据流中第一个文档形成第一个类簇

### 基于图分割的聚类

+ 计算文档对之间的相似度值，构建相似度图 G=(V,E)
    + 每个文档为图的一个节点
    + 文档之间有边连接，边的权重 W 为文档相似度
+ 文档聚类问题转换成在图上进行顶点分割的问题
+ 切割标准 min cut(A,B)
+ 问题
    + 只考虑了类簇之间的连接情况
    + 没有考虑类簇内部的密度
+ 改进方法: Normalized Cut

### 基于密度峰值的聚类(Science)

+ 简单优美，可自动确定聚类数目，检测孤立点，可识别不同形状的聚类
+ 假设: 类簇中心被一些局部密度较低的点围绕，并且这些点距离其他有高局部密度的点的距离都比较大
+ 聚类过程
    + 计算出所有数据点的局部密度值和到高局部密度点的距离后，可以得到一张决策图
    + 在决策图上挑选具有较大密度的样本点作为类簇中心
    + 将其他样本点按照局部密度从高到底依次确定所属类簇，其类簇为领域内最近的高于该点局部密度的样本点所处的类簇

### 半监督聚类

除了带聚类的数据，还提供了少量先验知识

+ 部分标注信息
    + 例如为若干数据点标注了类簇
+ 约束信息
    + 例如要求某两个数据点必须在同一类簇，或者某两个数据点不能在同一类簇
+ Seeded K-means
    + 用户提供了 Seeded points
    + 利用提供的标注信息(seeded points)寻找初始类簇中心，然后运行 K-means
    + Seeded points 的标签可能会改变
+ Constrained K-means
    + 用户提供了 Seeded points
    + 利用提供的标注信息(seeded points)寻找初始类簇中心，然后运行 K-means
    + Seeded points 的标签不允许被改变

### 聚类结果评估

+ 基于人工标注的类簇进行评价
+ 评价准则包括: F 值、纯度(Purity)、规范化信息(NMI)

### 聚类算法的选择

+ 聚类算法的选择具有挑战性
    + 每种算法都有各自的优势与不足，聚类效果通常依赖于聚类算法、距离函数、具体的数据与应用
+ 实际做法
    + 运行使用不同距离函数的多个聚类算法，分析和比较聚类结果
+ 对聚类结果的解释要基于原始数据的意义以及聚类算法的特性

### 半监督聚类

+ COP K-means
    + 用户提供了 must-link 与 cannot-link 约束
    + 初始化: 类簇中心随机选择，但必须保证满足 must-link 约束，也就是 must-link 的两个数据点不能选择做为不同类簇的中心
    + 算法: 一个数据点必须在不违反任何约束的情况下归属到临近的类簇

### 检索结果聚类

+ 两类方法
    + 先对 snippet 进行聚类，然后为每个类簇选择标签
    + 先分析获取有意义的类簇标签，然后将检索结果划分到不同标签
+ 基于后缀树的检索结果聚类(Suffix Tree Clustering, STC)
    + 时间复杂度低，高效
    + 容易获得每个类簇的关键词标签
    + 允许一个文档属于多个类簇
+ 基于回归学习的检索结果聚类
    + 现货的重要的短语代表类簇，然后再将检索结果跟类簇关联
    + 同样允许一文档隶属多个类簇
    + 候选短语(频率大于3的n-gram(n<=3))
    + 短语重要性排序
        + 看做回归问题
        + 利用 SVM-Light 实现的支撑向量回归等多个回归方法
        + 人工标注短语训练集，也即短语与其重要性分值
    + 短语特征
        + Phrase Frequency/Inverted Document Frequency(TFIDF)
        + Phrase Length
        + Intra-Cluster Similarity
        + Cluster Entropy
        + Phrase Independence

## 关联规则挖掘：定义

关联规则反映一个事物与其他事物之间的相互依存性和关联性。如果两个或者多个事物之间存在一定的关联关系，那么其中一个事物就能够通过其他事物预测到。关联规则表示了项之间的关系。

+ 给定一个记录集合，每个记录包含若干项
    + 产生依赖规则，可以基于某些项的出现预测一个项的出现

应用：市场营销

+ 假如发现一条规则
+ {面包圈..} -> {薯片}
+ 可以帮助提高薯片的销量

## 摘要

为数据集进行总结，提供一个简洁/紧凑的表示，包括可视化与报表生成

## 回归

+ 基于若干变量的值预测一个给定的具有连续值的变量的值
    + 假设一个线性或非线性的依赖模型
+ 举例
    + 基于广告开支预测新产品的销售额
    + 基于温度、湿度、气压等预测风速
    + 预测股票指数

为数据预测一个连续值，确定两种或两种以上变量间的相互依赖关系。

+ 最简单的情形: 一元线性回归
    + 只包括一个自变量 x 和一个因变量 y，且二者的关系可用一条直线近似表示
    + 回归分析的目标为找一个线性函数迎合训练数据
    + 可采用最小二乘法
+ 其他回归方法
    + Logistic 回归
    + 岭回归
    + 支持向量回归
+ 回归结果评价
    + 均方误差(Mean Squared Error, MSE)
    + 均方根误差(root mean square error, RMSE)

## 偏差/异常检测

+ 从正常行为中检测显著的偏差/异常
+ 举例
    + 信用卡欺诈检测
    + 网络入侵检测

## 数据挖掘工具

+ Free open-source software and application
    + Weka
    + GATE
    + Carrot2
    + NLTK
    + Orange
    + RapidMiner
    + KNIME
+ Commercial software
    + IBM InfoSphere Warehouse
    + Microsoft Analysis Services
    + SAS Enterprise Miner
    + STATISTICA Data Miner
    + Oracle Data Mining

## 数据挖掘的挑战

+ 可拓展性
+ 挖掘高维数据、高速数据流
+ 挖掘序列数据、时间序列数据
+ 从复杂、异构、网络化数据中挖掘复杂知识
+ 挖掘低质量数据
+ 安全性、隐私保护
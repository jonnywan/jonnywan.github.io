---
layout: post
keywords: blog
description: blog
title: "Dataming with R"
categories: [R]
tags: [R Dataming]
group: R
icon: file-alt
---
{% include codepiano/setup %}

## R语言基础

* 1、 R的数据结构
向量 c()
矩阵 matrix()
数组 arrary()
数据框 data.frame()
因子 factor()
列表 list()

* 2、变量处理
缺失值处理(is.na() na.omit())
日期格式处理(as.data(x,"format"))
数据类型判断与转换(is/as.numeric() character() vector() data.frame() factor() logical())
排序、合并、子集等(dataframe[order(-age)],rbind(),cbind())

## 挖掘算法的R快速实现

* 1、KNN分类算法R语言实现

{% highlight R %}
> data(iris3)
> train <- rbind(iris3[1:30,,1], iris3[1:30,,2], iris3[1:30,,3]) #选前30个数据为训练数据
> test <- rbind(iris3[31:50,,1], iris3[31:50,,2], iris3[31:50,,3])#剩下的为测试数据
> cl <- factor(c(rep("s",30), rep("c",30), rep("v",30)))
> knn(train, test, cl, k = 3, prob=TRUE) #进行KNN算法分类
> attributes(.Last.value)
{% endhighlight %}

* 2、C4.5算法求解决策树的R语言实现
{% highlight R %}
> library(RWeka)
> library(party)
> oldpar=par(mar=c(3,3,1.5,1),mgp=c(1.5,0.5,0),cex=0.3)
> data(iris)
> m1 <- J48(Species ~ ., data = iris)
> m1
> table(iris$Species, predict(m1))
> write_to_dot(m1)
> if(require("party", quietly = TRUE)) 
> plot(m1)
{% endhighlight %}
Theory:
1.手肘法判断K值:
在斜率变化由 快 -> 慢 的拐点之间，选择k的值。

2.推荐系统中的几种常用算法：
基于内容的推荐：内容特征表示，特征学习，推荐列表
基于系统过滤的推荐：群体智能，用户历史行为
基于关联规则的推荐：transaction，频繁项集和关联规则挖掘
基于效用推荐：效用函数的定义
基于知识的推荐：知识图谱的创建。（大鱼吃？）
组合推荐：实际工作中经常采用；每种推荐算法都有自己的使用场景，可以综合考虑

3.什么是关联规则
根据transactions，去看哪些商品会 “一同购买”； 找到产品的内部的逻辑关系

4.Apriori算法的流程是怎样的
k=1 --> 计算k项集的支持度；
去除低于min_support的项集
持续k++，直到项集为空，则k-1项集的结果为最终结果

5.Apriori算法存在哪些不足
无法找到物品数量上的对应关系
浪费计算空间和时间

6.可视化视图都有哪些方式
比较：条形，线性
联系：气泡图
构成：饼图
分布：柱图


Thinking
1:关联规则中的支持度、置信度和提升度代表的什么，如何计算?
支持度support：某item出现的次数/总transaction数之比；support越高表示该‘组合’出现的概率越大。
置信度confidence：naive bays 在发生A的条件下，发生B的概率 记做 A -> B
提升度lift: itemA的出现，对itemB的出现概率的提升度

2:关联规则与协同过滤的区别
关联规则基于transaction；CF基于用户behavior history（用户偏好）
商品组合使用购物篮分析（apriori算法）；CF计算相似度
关联规则基于transaction的频繁项集额挖掘，static
当下需求：关联规则
长期偏好：协同过滤

3:为什么我们需要多种推荐算法
多种推荐算法互相补充，在用户不同的实用阶段发挥作用

4:关联规则中的最小支持度、最小置信度该如何确定
实验法确定
经验系数：min_support = 0.01 ~ 0.5
min_confidence = 0.5 ~ 1
Lift: >1 即有贡献

5:如果通过可视化的方式探索特征之间的相关性
看图中各个参数之间的关系；比如：
比较：条形，线性
联系：气泡图
构成：饼图
分布：柱图

6.关联规则和基于内容的推荐：
关联规则：item-item之间的频繁项集推荐（transaction）（dynamic transaction）
内容的推荐：基于content（feature），找到物品和物品之间的相似度（static：feature之间的相似度）




Sample answer for thinking:
1. 关联规则中的支持度、置信度和提升度代表的什么，如何计算？

支持度就是几个关联的数据在数据集中出现的次数占总数据集的比重。或者说几个数据关联出现的概率。如果我们有两个想分析关联性的数据X和Y，则对应的支持度为:

$$Support(X, Y)=P(XY)=\frac{number(XY)}{num(AllSamples)}$$

一般来讲，支持度高的数据不一定构成频繁项集，但是支持度太低的数据肯定不构成频繁项集。

置信度体现了一个数据出现之后，另一个数据出现的概率，或者说条件概率，若有两个分析关联性的数据$X$和$Y$，$X$对$Y$的置信度为：

$$Confidence(X \gets Y) = P(X|Y)=\frac{P(XY)}{P(Y)}$$

举个例子，在购物数据中，纸巾对应鸡爪的置信度为40%，支持度为1%。则意味着在购物数据中，总共有1%的用户既买鸡爪又买纸巾;同时买鸡爪的用户中有40%的用户购买纸巾。

提升度表示含有Y的条件下，同时含有X的概率，与X总体发生的概率之比，即:

$$Lift(X⇐Y)=P(X|Y)/P(X)=Confidence(X⇐Y)/P(X)Lift(X⇐Y)=P(X|Y)/P(X)=Confidence(X⇐Y)/P(X)$$

提升度体先了X和Y之间的关联关系, 提升度大于1则X⇐YX⇐Y是有效的强关联规则， 提升度小于等于1则$X⇐Y$是无效的强关联规则 。一个特殊的情况，如果X和Y独立，则有$Lift(X⇐Y)=1$，因为此时$P(X|Y)=P(X)P(X|Y)=P(X)$。

2. 关联规则与协同过滤的区别

关联规则面向的是transaction，而协同过滤面向的是用户偏好（评分）。
协同过滤在计算相似商品的过程中可以使用关联规则分析，但是在有用户评分的情况下（非1/0），协同过滤算法应该比传统的关联规则更能产生精准的推荐。
协同过滤的约束条件没有关联规则强，或者说更为灵活，可以考虑更多的商业实施运算和特殊的商业规则。
3. 为什么我们需要多种推荐算法

推荐算法是一种信息过滤算法，单一的算法有时候并不能保证系统的多样性以及用户的个性化

4. 关联规则中的最小支持度、最小置信度如何确定

试出来的
5. 如果通过可视化的方式探索特征之间的相关性

皮尔逊系数
相关性系数
热力图

Sample answer 2:
Thinking1	关联规则中的支持度、置信度和提升度代表的什么，如何计算
支持度：商品组合购买次数/全部购买次数，商品组合出现频率越高，支持度越大，可以看成是商品组合被购买概率。
置信度：置信度(A→B)可以看成是P(B|A)=P(AB)/P(A)，同时购买A和B的次数/购买A的次数。
提升度：提升度(A→B)=置信度(A→B)/支持度(B)，支持度(B)是购买B的概率，置信度(A→B)是A条件下购买B的概率，比值反映A条件对购买B概率的影响，大于1有利，小于1不利，等于1无关

Thinking2	关联规则与协同过滤的区别
关联规则根据历史订单数据基于频繁项集找到商品关联关系，使用场景类似于捆绑关系
协同过滤根据用户或商品的偏好基于相似度找到相似的用户或商品，适用于个性化推荐

Thinking3	为什么我们需要多种推荐算法
单一推荐算法有局限性，比如协同过滤依赖偏好，还有冷启动问题，关联规则需要历史订单等，多种算法可以互相补充

Thinking4	关联规则中的最小支持度、最小置信度该如何确定
根据具体情况，可以从高到低取20个，也可以在0.01-0.5找合适的，最小置信度可能在0.5-1

Thinking5	如果通过可视化的方式探索特征之间的相关性
展示事物的排列顺序，比如条图。
查看两个变量之间关系，如气泡图。
每个部分所占整体的百分比，如饼图。
关心各数值范围包含多少项目，如柱图
可视化特征之间的相关系数，热力图
横向条形图对特征向量的重要程度进行可视化
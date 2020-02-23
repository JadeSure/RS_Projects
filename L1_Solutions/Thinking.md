# RS_Projects
1. the definition for AI:
the theory and development of computer systems able to perform tasks normally requiring human intelligence.
based data to solve problem. data --> model --> solve the problem

2. 7 steps for machine learning：
Data collection --> Data preparation：pre-processing（delete same data，typo, missing） --> model selection --> training model --> model estimation -->
Hyperparameter adjustment（adjust parameters except model eg. learning cycles and learning rate）--> prediction

3. Regression problem：prediction for continuous values；classification problem：classification for discrete values
Linear regression：f(x) = wx +b (system of linear equations)
Logistic regression: sigmod function；Binary classification problem，belong to[0,1]; eg.how many probability for the value belong to 1.

4.what does RS mean？
The recommendation system is a filtering system, which based on users' behaviour history; customize a info source；

5. Content-based filter
based on property of items，provide tag，calculate similarity for each other；
Depend on item property and content, rather than behaviour of purchasing, looking through history.

6.collaborative filtering
通过数据寻找和你相似的永华，通过他们的行为和他们喜欢的内容，对你进行推荐。
显性反馈数据:用户明确表示对物品的喜欢行为：评分，喜欢收藏，购买
隐形反馈数据：不能明确反映用户喜好的行为：浏览，停留时间，点击

5.推荐系统中的EE问题 （探索发现）
Exploitation: 展示以往感兴趣的内容
Exploration：尝试新的东西 （对一个八卦的用户适当的推荐一下学习的文章，用户有可能会点击进去进行学习）

6.既然内容相似度计算简单，能频繁更新，为什么还需要协同过滤算法呢？
collaborative filtering 是一种dynamic产生的，能根据用户的使用行为，实时推荐；
惊喜度，满意度，多样性，新颖性，商业目标等也是推荐系统所追求的，避免content based的内容过于单一；
content basd is suitable for 冷启动;

Sample answer: 
内容相似度只关注对象本身的特征，通过对对象进行建模或是标注标签，仅仅考虑物品的特征，而没有从用户的角度考虑；
协同过滤算法则是充分利用了大量用户的智慧，以提升整个系统的推荐能力；
从用户的角度出发，兴趣相近的用户可能会对同样的东西感兴趣（UserCF），用户可能较偏爱与其已购买的东西相类似的商品（ItemCF）

7. 你需要推荐系统么？哪些情况下不需要推荐系统？
不是所有情况都需要推荐系统。
less contents:推荐系统是一种信息过滤，即用户无法在有效的时间内浏览完所有信息，rs即可靶向推荐产品；
less connections with users and items:用户较少时，key points 是尽快拓展用户，建立用户与商品之间的联系。

sample answer:
在使用一些互联网产品时，如果是以内容为主的，是需要一些推荐系统的；
而对于一些初创产品或者小众产品，更重要的是如何第一眼将产品的亮点突出，甚至最好能够把所有最好的东西都展现出来，未必需要考虑对于用户的推荐。更应该考虑冷启动的问题，包括内容的冷启动和系统的冷启动，以吸收更多的新用户。

8. 如果给一个视频打标签，视频中有音乐作为背景音乐，采用了NLP方式对内容自动打标签，可能存在什么问题？
不准确；
背景音乐可能干扰NLP和关键字特征提取识别；BGM中的内容可能和video contents 完全不匹配，造成大量误判；
根据博主的视频方向进行tag，用该tag对视频，用户等进行分类和推荐。


Sample answer:
背景音乐中，可能会存在很多与实际视频内容不相关的主题（如搞笑或者没有意义的背景音乐），因此对于视频标签可能产生问题。

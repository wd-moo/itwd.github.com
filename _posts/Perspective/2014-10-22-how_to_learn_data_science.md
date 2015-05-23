---
layout: post
title: 如何学习数据科学
category: 学习观点
tags: [数据科学]
description: 个人对如何学习数据科学的一些个人认知，附录部分参考了网上资源
---

本文主要是个人对如何学习数据科学的一些个人认知，附录部分参考了网上资源。

<!-- more -->

###目录
{:.no_toc}

* 目录
{:toc}

###1.概述
数据科学(Data Science)是一门利用数据学习知识的学科，其目标是通过从数据中提取出有价值的部分来生产数据产品。它结合了诸多领域中的理论和技术，包括应用数学，统计，模式识别，机器学习，数据可视化，数据仓库，以及高性能计算。数据科学通过用运用各种相关的数据来帮助非专业人士理解问题。此外，数据科学并不局限于大数据，但是数据量的扩大诚然使得数据科学的地位越发重要。

数据科学的从业者被称为数据科学家。数据科学家通过精深的专业知识在某些科学学科解决复杂的数据问题。不远的将来，数据科学家们需要精通一门、两门甚至多门学科，同时使用**数学**，**统计学**和**计算机科学**的生产要素展开工作。所以数据科学家就如同一个team。

因此，学习数据科学是比较难的，因为你要学习不同的学科知识。这里只是简单地说说我个人对于学习数据科学的一些看法。对于数据科学，我对理论是比较看重的，所以不指望一本书学会或者一年内成为数据科学家。不过，想快速上手的人，可以更多的关注实践部分。

个人学习，其他部分主要涉及一些经济学、社会心理学等科学以进一步强化数据科学的应用。所有推荐书籍，可以自行网络搜索，推荐课程均为网络课程。

###2.理论

数据科学基础课程主要涉及**数学**，**统计学**和**计算机科学**。闲话少说，直奔主题：

####2.1 必修
- **统计学**  
这方面网络课程较多，比如[coursera](https://www.coursera.org/courses?orderby=upcoming&cats=stats)和[edx](https://www.edx.org/course-list/allschools/statistics-data-analysis/allcourses)上面都有很多课程，此外[网易公开课](http://c.open.163.com/search/search.htm?query=%E7%BB%9F%E8%AE%A1%E5%AD%A6&enc=%E2%84%A2#/search/course)也提供了很多相关课程，如果英语比较差，可以学习可汗学院的[统计学](http://v.163.com/special/Khan/khstatistics.html)。如果英语不错，推荐两门coursera课程，一门简单点[统计：让数据有意义](https://www.coursera.org/course/introstats)(多伦多大学公开课)，一门复杂点[数据分析与统计推断](https://www.coursera.org/course/statistics)(杜克大学公开课)。其中，杜克大学公开课更是数据分析的入门好课程，但是，练习量很大。
书籍的话，没什么特别推荐的。

- **概率论**  
网上课程也比较多，请自行到coursera、edx和网易公开课上搜索。我本人是可以直接学习*概率论与数理统计*课程，推荐书籍**《数理统计与数据分析-JohnA-Rice》**，这本书，计划多读几遍。

- **线性代数**  
也有人说*矩阵论*，可能是难度的区别，但是我更喜欢说线性代数。个人非常建议学好线性代数！网上课程也比较多，个人推荐网易公开课中的Gilbert Strang在MIT的课程[线性代数](http://v.163.com/special/opencourse/daishu.html)，教材推荐**《线性代数-利昂(Steven J.Leon)》**(中文版)，如果英语好的同学可以读英文版，此外Gilbert Strang老师的**《线性代数》**教材。

- **高等数学**  
大学都学过，复习一下就好。主要是优化、极限、微积分等。如果数学比较好，可以进一步尝试[凸优化-Stephen Boyd](http://web.stanford.edu/class/ee364a/lectures.html)。

- **数据挖掘**  
这方面书籍比较多，在线课程相对比较少。入门书籍推荐**《数据挖掘导论-Pang-Ning Tan》**，相对比较全面的介绍了数据挖掘的各个方面，对于算法层面，讲解的也比较简洁，比较浅显易懂。如果课程的话，建议学习**机器学习**。

- **机器/统计学习**  
课程非常多，资料非常杂而多，而且不同的书籍，观点不一。推荐基础课程斯坦福大学 Andrew Ng的[机器学习](http://v.163.com/special/opencourse/machinelearning.html)(网易公开课，偏理论，较老)和coursera上的[机器学习](https://www.coursera.org/course/ml)(偏应用，较新)。书籍的话，先把Ng的课件和notes看完吧。注意这门课是用matlab/octave作为编程工具。机器学习属于数据科学的核心技能，可以偏应用（会使用别人开发的包），也可以偏理论（能够自己实现算法并改进）。  
另外，斯坦福大学的Trevor Hastie和Rob Tibshirani的[统计学习](https://class.stanford.edu/courses/HumanitiesScience/StatLearning/Winter2014/about)，这门课小相对比较基础，使用R语言，教材**[《An Introduction to Statistical Learning with Applications in R》](http://www-bcf.usc.edu/~gareth/ISL/)**也是免费的，且入门性质的。  
网上有很多书籍，一般中文的推荐李航博士**《统计学习》**。但是英文版的书籍，主要有三本：一本是Bishop的**《Pattern Recognition And Machine Learning》**(PRML)，一本是Trevor Hastie、Rob Tibshirani等人的**[The Elements of Statistical Learning》](http://statweb.stanford.edu/~tibs/ElemStatLearn/)**(ESL)，一本是Kevin Patrick Murphy的**[《Machine Learning: a Probabilistic Perspective》](http://www.cs.ubc.ca/~murphyk/MLbook/)**(MLAPP)。 简单的说，PRML是偏向于贝叶斯学派来解释机器学习，适合研究生和博士等，也被用于很多本科院校的教材，难度稍微大。而ESL是偏向于频率学派来解释机器学习。MLAPP则是哈佛大学本科生的教材，观点介于频率和贝叶斯之间。

####2.2 选修
选修内容，我自己也没想好——应该是基础知识的进一步强化或者其他的一些技能。一般而言，这跟自己的选择的方向有很大的关系。比如从事大数据的话，那么需要学习hadoop或者spark等工具。但是，如果是图像处理，可能还需要学习一下深度学习的内容，甚至需要强化矩阵论等基础知识。另外，基础课程一般都对应着高级课程，比如机器学习的高级课程，advanced machine learning，也有高级统计学等课程。这方面，大家可以参考一些大神推荐的reading list。

###3.实践

####3.1基础工具
- **excel**：应该是最常见的，至少要会vlookup等函数、数据透视表和基本作图。其他高级点的类似工具有spss。
- **R语言**：在统计学和数据分析中，是比较值得推崇的，基本的数据清洗、建模、数据可视化等都有广泛应用。开源免费。这方面的教材也比较多，课程也很多。推荐coursera上面霍普金斯大学的数据科学专题教程中[数据分析](https://www.coursera.org/course/dataanalysis)，套装是都是用R语言的。
- **Python**：一般而言，数据分析师倾向于要求R语言，但是，Python在数据科学方面应用更广泛。
Python的基础课程推荐麻省理工的[计算机科学及编程导论](http://v.163.com/special/opencourse/bianchengdaolun.html)，可以配合这本**Python入门经典:以解决计算问题为导向的Python编程实践**一起使用。在数据科学方面，哈弗大学有[data science](http://cs109.org/)公开课，使用Python。另外，Python下有很多数据科学包，参考[pydata](http://pydata.org/)。
- **SQL**:基本的SQL语句还是必须要会的。此外，对于基本的数据库操作也是要有的，毕竟需要读取数据等操作。

上面是简单的介绍了一些工具。对于工具类的，网上有很多资源列表。大家可以自己去搜索一下相关电子书。此外，对于Python在数据分析和数据挖掘中的应用，书籍非常多，而且最近几年也是层出不穷。

####3.2高级工具
看行业需求，有的行业需求matlab、有的行业需求sas，有的行业需求hadoop、有的要求会C语言或者java。当然，一般也要会linux。

###4.其他
数据科学是一门综合学科，也是一门艺术，从业者也需要对业务和行业有非常好的认知和理解。这里推荐一些课外书籍，方便大家休闲时候阅读。《经济学的思维方式》、《社会心理学》、《市场营销》、《消费者行为》、《史记》、《战国策》等等书籍，此外，纪伯伦、泰戈尔等诗词散文诗也非常适合阅读。
数据科学，有时候可以认为是人性的科学！

###5.附录

####5.1 西北大学教学规划
位于伊利诺伊州芝加哥郊外埃文斯顿市的美国名牌私立大学——西北大学（Northwestern University），决定从2012年9月起在其工程学院下成立一个主攻大数据分析课程的分析学研究生院，并开始了招生工作。西北大学对于成立该研究生院是这样解释的：“虽然只要具备一些Hadoop和Cassandra的基本知识就很容易找到工作，但拥有深入知识的人才却是十分缺乏的。”

此外，该研究生院的课程计划以“传授和指导将业务引向成功的技能，培养能够领导项目团队的优秀分析师”为目标，授课内容在数学、统计学的基础上，融合了尖端计算机工程学和数据分析。课程预计将涵盖分析领域中主要的三种数据分析方法：预测分析、描述分析（商业智能和数据挖掘）和规范分析（优化和模拟），具体内容如下。

**(1) 秋学期**

* 数据挖掘相关的统计方法（多元Logistic回归分析、非线性回归分析、判别分析等）
* 定量方法（时间轴分析、概率模型、优化）
* 决策分析（多目的决策分析、决策树、影响图、敏感性分析）
* 树立竞争优势的分析（通过项目和成功案例学习基本的分析理念）

**(2) 冬学期**

* 数据库入门（数据模型、数据库设计）
* 预测分析（时间轴分析、主成分分析、非参数回归、统计流程控制）
* 数据管理（ETL（Extract、Transform、Load）、数据治理、管理责任、元数据）
* 优化与启发（整数计划法、非线性计划法、局部探索法、超启发（模拟退火、遗传算法））

**(3) 春学期**

* 大数据分析（非结构化数据概念的学习、MapReduce技术、大数据分析方法）
* 数据挖掘（聚类（k-means法、分割法）、关联性规则、因子分析、存活时间分析）
* 其他，以下任选两门（社交网络、文本分析、Web分析、财务分析、服务业中的分析、能源、健康医疗、供应链管理、综合营销沟通中的概率模型）

**(4) 夏学期**

* 风险分析与运营分析的计算机模拟
* 软件层面的分析学（组织层面的分析课题、IT与业务用户、变革管理、数据课题、结果的展现与传达方法）

####5.2 数据科学的经历和心得
本附录转自[博客文章](http://xccds1977.blogspot.com/2013/01/blog-post.html)，作者是一名软件工程师，他描述了在五年时间内学习数据科学的经历和心得，他的学习途径包括了自学（书籍、博客、小项目），课程学习，教学讨论，会议交流和工作实践。

**一、入门**

1）自学（2 - 4个月）

自学是起步的关键。两年前，我和几个同事组成了一个研究小组，讨论[统计202课程](http://stats202.com/)的学习材料。这让我感觉很兴奋，并由此开始数据分析的学习研究。研究小组有5名成员，但最后只有2个人选择去更深入地研究这个领域（数据科学并不适合每一个人）。

- 学习基本的统计知识：统计202课程是非常合适的入门资料
- 学习一种统计工具：作为一个菜鸟，我用了3个月的时间埋头学习[R语言](http://cran.r-project.org/)，R学起来非常有趣。（[为什么要学习R？](http://www.rcasts.com/2011/03/why-learn-r.html)(也有为什么学习Python！)）
- 解决一些好玩的小问题：好奇心是数据科学的关键。如果你对国家的经济问题，犯罪统计，体育成绩等感兴趣的话，去收集数据并开始回答你的问题吧。
- 学习Unix工具：我选择了O'Reilly出版的[数据之魅](http://shop.oreilly.com/product/9780596802363.do)作为学习材料。
- 学习SQL和脚本语言：我了解的有Java，Ruby和SQL。 Python也在我的名单上。

有很多的培训材料可以在网上找到：

- [统计202](http://www.stanford.edu/class/stats202/)
- [加州理工学院的数据科学课程](http://work.caltech.edu/telecourse.html)
- Coursera：[数据科学](https://www.coursera.org/course/datasci)，[机器学习](https://www.coursera.org/course/ml)，[数据分析](https://www.coursera.org/course/dataanalysis)，[数据分析计算](https://www.coursera.org/course/compdata)
- 加州大学伯克利分校 - [数据科学](http://datascienc.es/)
- 骑士新闻中心的课程：[资讯图像和数据可视化](http://open.journalismcourses.org/)
- 统计101：[Udacity（统计入门）](http://www.udacity.com/overview/Course/st101/CourseRev/1)，[可汗学院](https://www.khanacademy.org/math/probability/statistics)，[卡耐基梅隆大学的统计课程](http://oli.cmu.edu/courses/free-open/statistics-course-details/)
- [Learn R](http://tryr.codeschool.com/)

2）课堂训练（9 - 12个月）

如果你想认真提高这项技能，那就选择一门课程，严肃的对待它。斯坦福大学提供了很优秀的课程。

- [数据挖掘分析STATS202](http://www.stanford.edu/class/stats202/)
- [线性和非线性优化MS＆E211](http://www.stanford.edu/class/msande211/)
- [挖掘海量数据集CS246](http://www.stanford.edu/class/cs246/)
- [现代应用统计：STATS315A](http://www-stat.stanford.edu/~tibs/stat315a.html)
- 统计方法的金融应用STATS240P
- [现代应用统计：数据挖掘STATS315B](http://www.stanford.edu/class/stats315b/)

**二、聚焦**

- 1）集中所有精力
当我迷上了数据科学时，我发现只花20％的时间是不够的，这需要花100％的时间，所以我会去发现并解决工作中出现的所有和数据相关的问题（大数据分析，医疗保健，零售分析，优化问题）。
- 2）着手有趣的问题
把学习目标和个人兴趣放在一起。解决有趣的问题，同时学习新的技术是很有用的。例如我对零售，医疗保健和体育数据分析很有兴趣。
- 3）加速学习：
教学相长：我会给同事和朋友教一些R语言和数据挖掘的入门知识。这使我在这方面的知识更为扎实，也使得周围的人对这个主题更有兴趣。这对我来说也是一种回馈开源社区的方式。博客写作也是另一种学习和贡献的方式。
关注业内领袖：网络中有很多厉害的数据科学家，关注这些人可以得到很好的启发。例如： DJ Patil, Hillary Mason, Jeff Hammerbacher, Carla Gentry, Monica Rogati,Cathy O'Neil。
阅读有趣的博客：http://datascience101.wordpress.com，http://columbiadatascience.com/blog，http://www.r-bloggers.com，http://www.datawrangling.com，http:// flowingdata.com（Quora的最好的的数据博客列表）
定期参加聚会：本地的数据科学/ R聚会，这一领域的发展非常迅速，我至少每隔一年去那里。看看有什么好玩的新东西。
了解大数据技术：MapReduce / Hadoop，云计算。我尽量不使用任何商业技术供应商，现在回想起来，这是一个很好的决定。
- 4）了解业务领域知识
我很幸运，有机会接触到内部和外部的数据科学家，他们帮助我理解他们处理数据问题的方法。我从他们身上学到的“假设驱动的数据分析”，而不是“盲目加蛮力数据分析”的重要性。重点是理解的业务领域问题，然后再尝试从数据中提取有意义的见解。这使我了解一些运营，零售，旅游及物流收入管理和医疗行业。 “纽约时报”近日发表文章，强调有必要为直觉。

3、有用的数据科学读物

- [数据挖掘导论](http://www.amazon.com/Introduction-Data-Mining-Pang-Ning-Tan/dp/0321321367)
- [果壳中的R](http://www.amazon.com/Nutshell-Desktop-Quick-Reference-OReilly/dp/059680170X)
- [数据之魅](http://www.amazon.com/Data-Analysis-Open-Source-Tools/dp/0596802358)
- [可视化之美](http://www.amazon.com/Beautiful-Visualization-Looking-through-Practice/dp/1449379869)
- 查看更多的数据科学的书籍：[O'Reilly](http://shop.oreilly.com/category/get/data-science-kit.do)，[Manning](http://myemail.constantcontact.com/Data-Science-books-at-Manning.html?soid=1101335703814&aid=F6MCzlEavBM)

4、对我感觉没多大用的东西

- 学习多个统计工具：一年前，我开始有一些SAS编程的工作要求，我学了一个月左右的SAS，但没什么效果。主要的原因是学习惯性，而且我喜欢用R.我真的没有需要去学习另一种统计工具。R虽然不是完美的，但将R和其他我熟悉的软件工具结合，我可以解决所有数据的科学问题。因此，我的建议是，如果你已经知道了SAS，STATA，MATLAB，SPSS，STATISTICA，非常好，坚持下去。但是，如果你正在学习一种新的统计工具，那就选择R吧。
- 公开课程：我试图用Coursera来自定进度学习，但对我来说，这不是有效的。我需要有压力，有学分的正式课程。
- 过多的学习量：需要注意工作与生活的平衡。今年早些时候，我试图同时学习多门困难的课程，我很快就意识到这么干没什么好处。

####5.3 数据科学学习图谱

<img src="/images/resource/road_data_science.jpg" height="100%" width="100%">

最后引用Thomas H. Davenport（埃森哲战略变革研究院主任） 和 D.J. Patil（美国科学促进会科学与技术政策研究员，为美国国防部服务）的话来总结数据科学家需要具备的能力：

- 数据科学家倾向于用探索数据的方式来看待周围的世界。（好奇心）
- 把大量散乱的数据变成结构化的可供分析的数据，还要找出丰富的数据源，整合其他可能不完整的数据源，并清理成结果数据集。（问题分体整理能力）
- 新的竞争环境中，挑战不断地变化，新数据不断地流入，数据科学家需要帮助决策者穿梭于各种分析，从临时数据分析到持续的数据交互分析。（快速学习能力）
- 数据科学家会遇到技术瓶颈，但他们能够找到新颖的解决方案。（问题转化能力）
- 当他们有所发现，便交流他们的发现，建议新的业务方向。（业务精通）
- 他们很有创造力的展示视觉化的信息，也让找到的模式清晰而有说服力。（表现沟通能力）
- 他们会把蕴含在数据中的规律建议给Boss，从而影响产品，流程和决策。（决策力）
# 实习项目 (持续更新中)
自认为适合找实习、校招等，写在简历上的项目。写这个目的，是为了广大学子真正学到一些东西，并且助力于实习和校招。

github有这么多的资源，不如推荐点好东西给看到文章的各位。如果以学习为目标，那么其实一些培训班的视频和课程就很好，比如黑马、尚硅谷，这对一开始的学习很有帮助。

如果是以找一份实习为目标，也可以直接用培训班的项目，只不过大家都这么做的话，简历很重复而且没有亮点。

因为现在很多同学找实习，简历都是什么培训班的包装项目，真的看腻了，比如：什么外卖、什么商城、什么论坛、又或者是什么RPC，还有什么DDD抽奖系统、6.824、6.828之类的。。当然不是说这些不好，只是有点审美疲劳。

所以本仓库的目的，就是为了寻找一些比较小众，但是又适合学习、以及写入简历的项目。（后续会持续更新，可以关注一下呀~）

觉得不错的，点个右上角点个星星吧~
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
## AI

### 大模型相关
这方向非常的热门，也非常的火，门槛高。因为如果是普通后端项目，在本地跑起来并不困难，对机器的要求比较低，但是很多ai infra相关的项目，比如多卡训练，十亿参数的模型微调，多卡推理，其实在本地运行起来都非常困难。即使把代码公开给了用户，用户也只能看看，但是很难真正的去入手，去了解为什么这个训练参数要这么改，怎么跑多卡推理，怎么做量化和蒸馏。这些都是个人学习中难以掌握的内容。

#### 6.5940

这是我看下来，感觉最适合初学者学习的项目。主题包括模型压缩、修剪、量化、神经架构搜索、分布式训练、数据/模型并行、梯度压缩和设备端微调。还介绍了适用于大型语言模型和扩散模型的特定于应用程序的加速技术。还有相关实验，将在笔记本电脑上实现模型压缩技术和部署大型语言模型 （Llama2-7B） 的实践经验。

官网链接：https://hanlab.mit.edu/courses/2024-fall-65940

bilibili视频链接：https://www.bilibili.com/video/BV1fb421q7Ut

#### （非广告）书生大模型实战营

这个项目还行，可以尝试报名参加，会给你云服务器，让你学习如何进行简单的微调、部署。整体来说难度并不高。不过b站也有免费的视频可以看，整体来说还是能学到不少东西

官网链接：https://github.com/InternLM/tutorial

bilibili视频链接：https://space.bilibili.com/1293512903


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
## 后端
### Java

一般说后端，多半都是Java。但是后端项目很多，怎么找到比较出彩的项目，并且写到简历上，比较困难。这里会列出一些比较少见的项目，但是质量也不错，很适合初步学习。

#### 企业广告系统
https://github.com/SnoopyWolf007/link-advertise

是面向企业广告投放链式跟踪的开源系统。作用类似于把广告投放出去，然后追踪广告投放效果的系统，然后查看转化率等等。这个系统比较贴合广告架构中，比较精细的一部分，很适合深入学习，可能用这个来找到对应的实习或者校招，值得高度推荐。


#### 商城系统
https://github.com/xmchengyuxin/lekshop

后端基于SpringBoot 研发，前端使用 Vue、uniapp开发， 系统全端全部代码开源。适合学习了谷粒商城之类的培训班课程的后续学习。因为很多培训班项目的目的是教会你，用的东西大而全，多而杂。这个项目比较小而且精，很适合用于面试。

### 推荐系统

不得不说，搜广推是互联网的唯一真神。这个方向基本不愁没有工作，跳槽也很好，所以第一份工作尽可能往这方面靠，是最好的。

下面推荐的比较适合用于找实习，校招也行，看个人理解程度

#### monolith
https://github.com/bytedance/monolith

字节跳动的推荐系统实践，学习起来难度颇高，不适合没有基础的学。但是整体质量确实相当的高，学完直接校招不成问题。


#### 商品实时推荐系统
https://github.com/water8394/flink-recommandSystem-demo


这个比较偏大数据方向的数据工程，主要使用Flink，用来找大数据方向的实习非常好用


#### AMS实时推荐系统
https://github.com/XBaith/ams-recommendation-system 


这个也是推荐系统，但是也涉及到了后端，有一些消息队列的操作，比较全面

### Go

#### 社区
https://github.com/TengFeiyang01/webook

仿小红书项目，作者的项目说明写的非常详细，而且还教了怎么用k8s部署，目前也在持续更新，值得学习

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
## 基础架构
### 向量数据库
https://github.com/asdadeeeee/vectorDB
a vector database implementation based on 《从零构建向量数据库》；
支持FaissIndex，HnswlibIndex； 支持标量向量混合查询； 支持数据持久化存储； 使用http请求对数据库发起访问，插入或查询vector

虽然DB赛道非常的饱和，但是结合向量查询，往大模型靠，还是有前景的，这个项目不会太难，因为也有书本参考，比较新颖

### C++

C++方向的项目其实不太好找，因为C++本身就很难。而且不像Java那样有SpringBoot这种成熟的框架，C++做后端开发本身就比较少，更多是做基础设施。所以这里推荐的项目会更偏向于基础设施方向，适合对系统编程感兴趣的同学。

#### C++ Web框架
https://github.com/drogonframework/drogon

一个基于C++17的高性能HTTP框架，据说在Web框架性能测试中排名很高。非常适合学习现代C++开发，而且项目代码组织得非常好，适合阅读和学习。如果找C++后端的实习，这个写在简历上比较亮眼。

#### Muduo网络库
https://github.com/chenshuo/muduo

陈硕大佬写的网络库，虽然比较老但是经典中的经典。如果你要找C++后端或者网络编程方向的实习，muduo几乎是必学的。代码量不大，但是涉及到的知识点非常多，Reactor模式、one loop per thread、多线程编程、TCP编程等等。学完之后面试基本没有网络编程方面的问题了。

#### 分布式KV存储
https://github.com/youngyangyang04/KVstorageBase

一个基于跳表实现的KV存储引擎，支持多线程并发读写。项目不大，但是覆盖了C++很多核心知识点，适合写在简历上。也有配套的视频教程，比较友好。


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## 前端

前端方向的项目比较特殊，因为前端很容易写出页面来，但是很难写出有深度的项目。培训班一般教的都是各种后台管理系统、商城之类的，面试官看到太多了。这里推荐一些比较小众、但是能体现前端深度的项目。

### 低代码/设计工具方向

#### 阿里低代码引擎
https://github.com/lowcode-engine/lowcode-engine

阿里开源的低代码引擎，项目质量非常高。涉及到的知识点非常多：编辑器架构设计、插件体系、拖拽系统、schema驱动渲染、属性面板设计等等。这个项目比较复杂，但是学习其中的一两个模块就能在面试中脱颖而出。如果你想做前端基础架构或者工具链方向的实习，这个项目非常合适。

#### Formily
https://github.com/alibaba/formily

阿里开源的表单解决方案，核心亮点是响应式表单状态管理和JSON Schema驱动。学习这个项目可以深入理解：响应式编程原理、表单联动机制、JSON Schema协议、组件抽象设计。相比一般的表单项目，这个项目的架构设计深度要高很多。

#### Onlook
https://github.com/onlook-dev/onlook

一个面向设计师的开源AI-first设计工具，可以用AI可视化的方式构建React应用。项目使用TypeScript开发，涉及到Canvas渲染、AST操作、AI集成等前端进阶技术。比较新颖，目前还在活跃开发中，适合学习现代前端+AI的结合。

### 可视化/编辑器方向

#### Artalk评论系统
https://github.com/ArtalkJS/Artalk

一个自托管的评论系统，前端纯Vanilla JS实现（~40KB），后端用Go。前端部分涉及的技术点包括：组件化开发（无框架依赖）、Markdown渲染、无限滚动、嵌套分页列表、图片懒加载、插件扩展机制等。项目代码量适中，非常适合用来学习如何不依赖框架从零构建一个完整的前端应用。

#### IT-Tools
https://github.com/CorentinTh/it-tools

一个面向开发者的在线工具集合（Vue3开发），包含加密、编解码、时间转换等各种实用小工具。项目结构清晰，适合学习Vue3 + TypeScript的项目组织方式。虽然单个工具功能简单，但是整个项目的架构设计、组件复用、类型系统等都值得学习。


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## AI / 数据工程

数据工程是AI落地中非常重要的一环，但是很多同学只关注模型本身，忽略了数据管道和特征工程。这个方向找实习其实需求很大，尤其是搜广推方向的数据工程岗位。

### 数据管道

#### Data Engineering Zoomcamp
https://github.com/DataTalksClub/data-engineering-zoomcamp

一个免费的9周数据工程课程，覆盖了完整的数据工程栈：Docker、Postgres、GCP、Terraform、Airflow、BigQuery、dbt、Spark、Kafka等。非常适合零基础入门数据工程，课程设计非常系统。学完之后，基本的ETL、数据仓库、流式处理都能上手了。

#### Mage
https://github.com/mage-ai/mage-ai

一个开源的数据管道工具，用Python开发。可以用来构建、运行和管理数据管道，支持数据集成和转换。相比Airflow，Mage的界面更加友好，上手更快。学习这个项目可以了解：数据管道编排、任务调度、数据血缘追踪等概念。

### 特征工程

#### Feast
https://github.com/feast-dev/feast

开源的特征存储（Feature Store），用于AI/ML。这个项目在搜广推方向非常重要，因为特征工程是推荐系统的核心环节。学习Feast可以了解：特征服务化、在线/离线特征、特征回填、特征监控等概念。如果想找推荐系统方向的实习，了解Feature Store是很大的加分项。

#### GrowthBook
https://github.com/growthbook/growthbook

开源的Feature Flag和A/B测试平台。在互联网公司，Feature Flag和实验平台是基础设施中非常重要的一环。学习这个项目可以了解：特性开关、A/B测试统计方法、实验流量分配等知识。这个项目比较小众，写在简历上比较独特。

### RAG应用

#### Langchain-Chatchat
https://github.com/chatchat-space/Langchain-Chatchat

基于Langchain和大语言模型的RAG与Agent应用，支持本地知识库问答。涉及到的技术点非常多：文档加载、文本分割、向量化检索、Agent工具调用、多模型接入等。整个项目流程完整，从文件加载到文本分割到向量检索到LLM生成回答，非常适合用来学习RAG系统的完整实现。


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## Go / DevOps

Go语言在DevOps和基础设施领域几乎是统治地位，Docker、Kubernetes、Terraform都是Go写的。所以学Go的同学，做DevOps方向的项目是最自然的选择。

### 自托管平台

#### Gitea
https://github.com/go-gitea/gitea

一个轻量级的自托管Git服务，用Go开发。从Gogs fork而来，但已经发展得非常成熟。项目涉及到的技术点：Git协议实现、SSH密钥管理、Web Hook系统、CI/CD Pipeline、API设计、权限管理等。代码质量很高，社区活跃，适合深入学习Go的Web开发最佳实践。

#### 1Panel
https://github.com/1Panel-dev/1Panel

现代化的Linux服务器运维面板，Go + Vue开发。涉及Docker管理、网站部署、应用商店、防火墙配置、SSL证书管理等。项目国内团队开发，文档完善，社区活跃。适合学习Go后端 + 前端配合的全栈项目。

#### Dokploy
https://github.com/Dokploy/dokploy

开源的PaaS平台，类似Vercel/Netlify的自托管替代方案。TypeScript开发，但架构设计值得学习：Docker Compose编排、Traefik反向代理集成、多节点部署、数据库管理、实时监控等。如果你想学习PaaS/部署平台的设计，这个项目比直接看Vercel的代码要容易上手得多。

### CI/CD工具

#### act
https://github.com/nektos/act

用Go开发的工具，可以在本地运行GitHub Actions。这个项目巧妙地利用Docker API来模拟GitHub Actions的运行环境。学习这个项目可以深入了解：GitHub Actions的工作原理、Docker API的使用、CI/CD Pipeline的设计等。Go代码质量很高，适合学习Go的CLI工具开发。

#### Kestra
https://github.com/kestra-io/kestra

事件驱动的编排和调度平台，Java开发。虽然不是Go项目，但是在DevOps领域很有价值。支持工作流编排、任务调度、实时监控等。如果你同时懂Java和DevOps，这个项目在简历上会很亮眼。


&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## 算法
### 搜推算法
找搜广推算法方向的工作，是不用发论文的，猛猛学就完事了，工资都是top级别的



#### 音乐推荐系统demo
https://github.com/GoAlers/Music-Top-Recommend
这个是用Python写的，一些算法实现，作者还写了很长很长的文章去教会你，非常好用


### 相关论文
##### Recommenders
https://github.com/recommenders-team/recommenders
Recommenders 是Linux 人工智能与数据基金会下的一个项目。此存储库包含构建推荐系统的示例和最佳实践，以 Jupyter 笔记本的形式提供。

这个仓库展示了一些协同过滤，以及内容过滤算法的论文实现，整体来说比较简单，学会了就可以面试了，性价比还是很高的。




&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
## 想要什么方向的，往issue提，我尝试找找
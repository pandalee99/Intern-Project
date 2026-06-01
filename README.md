# 实习项目 (持续更新中)

自认为适合找实习、校招等，写在简历上的项目。写这个目的，是为了广大学子真正学到一些东西，并且助力于实习和校招。

github有这么多的资源，不如推荐点好东西给看到文章的各位。如果以学习为目标，那么其实一些培训班的视频和课程就很好，比如黑马、尚硅谷，这对一开始的学习很有帮助。

如果是以找一份实习为目标，也可以直接用培训班的项目，只不过大家都这么做的话，简历很重复而且没有亮点。

因为现在很多同学找实习，简历都是什么培训班的包装项目，真的看腻了，比如：什么外卖、什么商城、什么论坛、又或者是什么RPC，还有什么DDD抽奖系统、6.824、6.828之类的。。当然不是说这些不好，只是有点审美疲劳。

所以本仓库的目的，就是为了寻找一些比较小众，但是又适合学习、以及写入简历的项目。（后续会持续更新，可以关注一下呀~）

觉得不错的，点个右上角点个星星吧~

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## 关于"项目"这件事

先说清楚一个关键问题：**你简历上的项目，应该是你自己动手写的，而不是拿一个知名框架照着文档跑了一遍。**

比如你简历上写"Spring AI Alibaba"，面试官一看就知道这是阿里开源的框架，你只是调了几个API跑了个demo。这不叫项目，这叫"我读了个文档"。

真正适合写在简历上的项目，应该是：
- 你自己从零开始写的，或者基于某个小项目做了有意义的改造
- 有明确的技术难点，面试的时候你能讲出"我遇到了什么问题、怎么解决的"
- 代码量可控，你能理解每一行代码
- 面试官没见过一模一样的，不会审美疲劳

所以下面的推荐思路是：你可以自己做出来的方向 + 参考学习的小众项目，而不是直接让你拿个大框架当自己作品。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## AI

### 大模型推理引擎

这个方向门槛高，但也是目前最硬核最缺人的方向。关键是——你不能直接拿vLLM或SGLang这种几万行的工业框架写简历，面试官会问"你写的哪部分？"你答不出来。

正确的做法是：先学原理，然后自己写一个mini版的推理引擎。

#### Mini-SGLang（学习参考）

SGLang官方出的精简版，5000行Python，把RadixCache、Chunked Prefill、Overlap Scheduling、Tensor Parallelism这些核心机制全实现了。代码质量高，类型标注完整。不是让你拿它写简历的，是用来学的。 你学完它的核心原理之后，自己动手写一个只有PagedAttention+连续批处理的极简推理引擎，这才叫你的项目。

链接：https://github.com/sgl-project/mini-sglang

#### nanovllm（学习参考）

极简的vLLM实现，代码量非常少。还有人在此基础上做了逐行注释版（tinyvllm），非常适合理解LLM推理引擎的核心逻辑。

链接：https://github.com/a710128/nanovllm-voxcpm

注释版：https://github.com/out-or-outstanding/tinyvllm

#### 你可以做的项目：手写一个mini推理引擎

看完Mini-SGLang和nanovllm之后，自己动手写一个。起步版只需要实现：
- 基础的token生成（基于HuggingFace模型）
- KV Cache管理（不用PagedAttention那么复杂，先做一个简单的block管理）
- 连续批处理（continuous batching）
- OpenAI兼容的HTTP API

这样就够了。面试的时候你能讲清楚："我参考了Mini-SGLang的RadixCache思路，自己实现了一个简化版的KV Cache复用机制，在重复prefix的场景下吞吐提升了XX%。"这比写"我用了vLLM"要有说服力一百倍。

进阶版可以加上：
- Prefix Cache（复用共享前缀的KV Cache）
- Chunked Prefill（长序列分段处理）
- 简单的量化支持（INT8/INT4）

#### 6.5940（系统学习）

MIT的课程，如果你想把理论基础打好，这是最好的选择。主题覆盖模型压缩、修剪、量化、NAS、分布式训练、数据/模型并行等，还有在笔记本电脑上跑的实验（部署Llama2-7B）。学完之后你对整个AI Infra的理解会非常扎实，面试的时候能从原理层面回答问题。

官网链接：https://hanlab.mit.edu/courses/2024-fall-65940

bilibili视频链接：https://www.bilibili.com/video/BV1fb421q7Ut

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

### 大模型原理：从零手写

如果你想真正理解大模型是怎么运作的，而不是停留在"调API"的层面，那最好的方式就是从零写一个。

#### LLMs-from-scratch（学习参考）

Sebastian Raschka写的，从零用Python手写一个GPT-like的LLM。不是调用任何框架，是真的从矩阵乘法开始写。包含完整流程：tokenizer、attention机制、transformer层、预训练、微调，全都是手写的。配套的Manning出版的书非常详细。学完这个你对LLM内部原理的理解会非常深——面试的时候问你"self-attention的数学原理是什么"，你能从矩阵运算层面讲清楚，而不是背概念。

链接：https://github.com/rasbt/LLMs-from-scratch

#### nanoGPT（学习参考）

Karpathy大佬写的，最简洁的GPT训练代码。就一个文件，几百行Python，能跑出一个小型GPT。代码极其易读，适合快速理解"训练一个GPT到底需要什么"。和LLMs-from-scratch的区别是：那个更系统更详细，这个更精炼更直觉。建议先看nanoGPT建立直觉，再看LLMs-from-scratch深入细节。

链接：https://github.com/karpathy/nanoGPT



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

### 大模型微调

微调方向的项目也要注意——"我用LLaMA-Factory微调了一个模型"不算项目，因为那只是调了个工具。真正有价值的是你理解了微调背后的原理，并且做了有意义的实验对比。

#### LLaMA-Factory（做实验的工具）

统一微调框架，支持100+模型，有WebUI和Colab教程。**不是让你当项目写的**，而是让你高效地做微调实验的工具。

链接：https://github.com/hiyouga/LLaMA-Factory

#### 你可以做的项目：微调实验+性能分析

用LLaMA-Factory作为工具，自己做一套系统的微调实验：
- 选一个开源小模型（Qwen2-1.5B之类的，单卡就能跑）
- 在某个具体任务上（比如代码生成、对话摘要、领域问答），用LoRA微调
- 对比不同参数设置的效果：rank值、学习率、数据量、训练步数
- 记录训练loss曲线、评估指标变化、推理性能（吞吐/延迟）
- 做一个简单的量化（INT8/INT4），对比量化前后的精度损失和推理速度

简历上写"我在Qwen2-1.5B上做了LoRA微调实验，系统对比了不同rank值对下游任务的影响，发现在rank=16时效果最好而rank=64反而过拟合，同时INT4量化只损失了2%精度但推理速度提升了3倍"。面试官一听就知道你真的做过实验，不是抄的。

#### （非广告）书生大模型实战营

这个项目还行，可以尝试报名参加，会给你云服务器，让你学习如何进行简单的微调、部署。整体来说难度并不高。不过b站也有免费的视频可以看，整体来说还是能学到不少东西。

官网链接：https://github.com/InternLM/tutorial

bilibili视频链接：https://space.bilibili.com/1293512903

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

### AI Agent

Agent方向火，但"我用LangChain写了个Agent"已经烂大街了。面试官看到LangChain的项目太多了。要做Agent方向的项目，你得有自己的思考在里面。

#### 你可以做的项目1：手写一个简易Agent框架

不用LangChain，不用Spring AI Alibaba，自己从零写。核心只需要：
- 一个LLM调用模块（对接OpenAI API或者本地Ollama）
- 一个工具注册和调用机制（Tool Definition + Tool Execution）
- ReAct循环（Thought → Action → Observation → 继续/结束）
- 简单的对话记忆（Memory）

Python大概2000行就能搞定，Java用Spring Boot也差不多。面试的时候你能讲清楚："我参考了ReAct论文的思路，自己实现了Thought-Action-Observation循环，工具调用用的是JSON Schema描述，记忆用的是滑动窗口截断。"这才是你自己的项目。

参考学习：AgentScope（https://github.com/agentscope-ai/agentscope）——阿里的Agent框架，2.0版本比较成熟，可以看看它的设计思路，但别照抄。

#### 你可以做的项目2：特定领域的Agent应用

比框架更亮眼的是具体的应用。比如：
- 一个代码审查Agent：自动读你提交的代码，给出review意见（调用LLM + AST解析）
- 一个面试模拟Agent：扮演面试官提问，根据你的回答调整难度
- 一个论文总结Agent：读PDF → 提取关键信息 → 生成结构化摘要

这些项目面试的时候能讲出很具体的故事："我做了一个代码审查Agent，遇到的最大问题是LLM经常给出不准确的建议，我加了AST校验层，先用Python的ast模块做静态分析，确认问题真的存在后才输出。"

参考学习：Langchain-Chatchat（https://github.com/chatchat-space/Langchain-Chatchat）——可以看它的RAG流程设计思路。

#### 你可以做的项目3：Java版Agent框架

如果你是Java选手，不想用LangChain4j这种现成框架当简历项目，那就自己写一个。用Spring Boot，实现：
- 对接一个LLM API（OpenAI或Ollama）
- 工具定义和调用（用Java反射或者手写JSON Schema）
- ReAct循环
- 对话记忆（存Redis或数据库）
- 简单的Web界面（用Thymeleaf或Vue）

Java版Agent框架市面上很少有人自己从头写，这本身就足够独特。面试官问"为什么不直接用LangChain4j？"你可以回答："我想理解Agent的核心机制，而不是只学会调API。自己写了一遍之后，我清楚了ReAct循环的边界情况怎么处理，比如工具调用失败的时候怎么回退。"这就很有说服力了。

参考学习：LangChain4j（https://github.com/langchain4j/langchain4j）——可以看看它的接口设计思路，但核心逻辑自己写。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

### RAG系统

"我用LangChain做了个RAG"也是烂大街了。但如果你自己做了一个RAG系统，并且在检索质量上做了改进，那就不一样了。

#### 你可以做的项目：手写RAG + 检索质量优化

自己从零搭建（不用LangChain），核心模块：
- 文档加载和切分（PDF/Markdown/HTML）
- Embedding生成（调用API或本地模型）
- 向量存储（用Milvus/Qdrant或者自己写一个简单的基于Faiss的存储）
- 检索 + 重排序（先向量检索top-k，再用LLM做Rerank）
- 生成回答（带引用溯源）

亮点在于你可以做检索质量的对比实验：
- 不同切分策略（固定长度 vs 语义切分）的检索精度对比
- 向量检索 vs 混合检索（向量+关键词BM25）的效果对比
- 加Rerank vs 不加Rerank的精度提升
- 不同Embedding模型的效果对比

这些实验数据写在简历上，面试官一看就知道你不是抄了个demo，而是真的对RAG的每个环节都做了思考。

参考学习：Langchain-Chatchat（https://github.com/chatchat-space/Langchain-Chatchat）——看它的RAG流程，但核心自己实现。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

### "从零构建"系列

Feynman说过："What I cannot create, I do not understand." 下面这些"从零构建"的项目，每一个都适合写在简历上，因为面试官知道你理解了底层原理，而不是只会调框架。

#### 你可以做的项目：手写一个mini向量数据库

现在向量数据库是AI应用的核心基础设施，但Milvus、Qdrant这种项目代码量太大。你可以自己写一个mini版的，只需要实现：
- HNSW索引（近似最近邻搜索的核心算法）
- 向量的增删改查
- 标量+向量混合查询
- 简单的持久化存储
- HTTP API

代码量大概2000-3000行，面试的时候你能讲清楚HNSW的层级结构怎么建的、搜索时怎么从顶层往下找的、为什么比暴力搜索快。这个方向目前还比较小众，写在简历上很独特。

参考学习：vectorDB（https://github.com/asdadeeeee/vectorDB）——基于《从零构建向量数据库》一书的实现，还有书可以参考。

#### 你可以做的项目：手写一个mini消息队列

Kafka太大了看不动，自己写一个mini版。核心实现：
- 基于文件的持久化存储（append-only log）
- 生产者/消费者模型
- Consumer Group的概念
- 简单的分区机制
- 零拷贝优化（可选进阶）

Java实现的话，Netty做网络层，内存映射文件做持久化，大概3000行代码。面试的时候讲"我自己实现了一个基于mmap的append-only log存储引擎，对比了mmap和普通FileIO的写入性能差异，mmap在高吞吐场景下快了2倍"。找后端实习的时候这个项目非常能打。

参考学习：build-your-own-kafka（https://github.com/buildthingsuseful/build-your-own-kafka）——Java从零构建Kafka的教程。

#### 你可以做的项目：手写一个mini Docker容器

用Go写，核心只需要：
- Linux Namespace隔离（PID/Network/Mount）
- Cgroup资源限制
- 简单的镜像层管理（UnionFS）
- 命令行工具

代码量大概1000-2000行Go。面试的时候你能讲清楚"我用了PID Namespace实现了进程隔离，用Cgroup限制了内存和CPU使用，镜像层用的是overlayfs"。找云原生/基础设施方向的实习，这个项目比什么商城系统亮眼一万倍。

参考学习：
- Bocker（https://github.com/p8952/bocker）——100行bash实现的Docker
- Build a container in Go（https://www.infoq.com/articles/build-a-container-golang/）

#### 你可以做的项目：手写一个mini Git

用C/C++/Go/Java都行，核心实现：
- blob/tree/commit对象模型
- 简单的内容寻址存储（SHA-1哈希）
- 分支和合并（快进合并 + 三路合并）
- 基本的diff算法
- 命令行工具（init/add/commit/branch/checkout/log）

这个项目看起来简单但细节很多，面试的时候能讲清楚Git的内部数据结构，比如"Git的分支本质上就是一个指向commit对象的指针文件"，面试官会对你刮目相看。

参考学习：build-your-own-x里的Git章节（https://github.com/danistefanovic/build-your-own-x#build-your-own-git）

#### 你可以做的项目：手写一个简易搜索引擎

核心实现：
- 网页爬取（简单的HTTP爬虫）
- 倒排索引构建
- TF-IDF / BM25排序
- 简单的PageRank
- Web查询界面

这个项目的好处在于它涉及的面很广：爬虫、索引构建、排序算法、Web开发，每一块都有技术深度可讲。面试的时候你可以说"我的搜索引擎用了BM25排序，在1万篇文档的数据集上平均查询时间50ms"，这比空讲理论强多了。

参考学习：build-your-own-x里的Search Engine章节（https://github.com/danistefanovic/build-your-own-x#build-your-own-search-engine）

#### 你可以做的项目：手写一个mini Redis

用Go或C++实现，核心：
- 简单的KV存储（字符串、列表、哈希）
- 过期机制（TTL）
- 持久化（RDB或AOF，选一个实现就行）
- 简单的事件循环（epoll/kqueue）
- RESP协议解析
- 命令行客户端

这个项目找后端实习非常实用，因为Redis几乎是所有后端面试必问的。你能讲清楚"我用epoll实现了一个事件驱动的网络模型，支持RESP协议解析，AOF持久化用的是后台线程异步刷盘"。面试官问Redis底层原理的时候你再也不怕了。

参考学习：
- Build Your Own Redis from Scratch（https://build-your-own.org/redis）——有完整教程和书
- Python版mini Redis（http://charlesleifer.com/blog/building-a-simple-redis-server-with-python/）

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## 后端
### Java

一般说后端，多半都是Java。但是后端项目很多，怎么找到比较出彩的项目，并且写到简历上，比较困难。这里会列出一些比较少见的项目，但是质量也不错，很适合初步学习。

#### 企业广告系统
https://github.com/SnoopyWolf007/link-advertise

是面向企业广告投放链式跟踪的开源系统。作用类似于把广告投放出去，然后追踪广告投放效果的系统，然后查看转化率等等。这个系统比较贴合广告架构中，比较精细的一部分，很适合深入学习，可能用这个来找到对应的实习或者校招，值得高度推荐。

（⚠️ 该仓库链接目前似乎不可访问，可能已迁移或删除，建议搜索确认最新地址）

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

（⚠️ 仓库已迁移至：https://github.com/xxubai/ams-recommendation-system）

这个也是推荐系统，但是也涉及到了后端，有一些消息队列的操作，比较全面

### Go

#### 社区
https://github.com/TengFeiyang01/webook

仿小红书项目，作者的项目说明写的非常详细，而且还教了怎么用k8s部署，目前也在持续更新，值得学习

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## 基础架构
### 向量数据库
https://github.com/asdadeeeee/vectorDB

a vector database implementation based on 《从零构建向量数据库》；支持FaissIndex，HnswlibIndex；支持标量向量混合查询；支持数据持久化存储；使用http请求对数据库发起访问，插入或查询vector

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
#### Recommenders
https://github.com/recommenders-team/recommenders

Recommenders 是Linux 人工智能与数据基金会下的一个项目。此存储库包含构建推荐系统的示例和最佳实践，以 Jupyter 笔记本的形式提供。

这个仓库展示了一些协同过滤，以及内容过滤算法的论文实现，整体来说比较简单，学会了就可以面试了，性价比还是很高的。

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;

## 想要什么方向的，往issue提，我尝试找找
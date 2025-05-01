# Hierarchical Indexing for Retrieval-Augmented Opinion Summarization （HIRO）


## Task Definition

将针对一个话题的大量的，多样化的用户评价。自动汇总成一个完整的，单一的，易于理解的摘要。


## 潜在的可能可以阅读的论文（引用）

- LLM倾向于对开始和结束的内容进行总结（2023）：Lost in the middle: How language models use long contexts.
- 一种去噪自动编码器（2023 ACL）：Attributable and scalable opinion summarization
- 残差矢量量化技术是个什么玩意？？

## Contribution

- 一种编码方式，适用于语义层次结构
- 从该离散结构表示中找到中心点（相关句子，流行句子）
- 一个自动指标：是否是流行的通用的句子，非通用的句子的惩罚
- 人工评估指标结果（这个可以详细看）
  


## Introduction

一个好的摘要：突出最流行观点，忽略掉一些细节，有助于区分不同的观点的差异化（AB想法各有千秋）


## Hierarchical Indexing

总结来讲就是主题相同的放在同一个高维度，语义相似放在同一个分支

### 刚看到这里的时候产生的一些QA：

- 这个分支的初始化是怎么实现的，结构是怎么样的？
- 表示空间的正负样本是怎么来的?
- 表示空间是怎么训练的？
- 为什么不能用语义相似度来进行所谓的聚类分析，而是创建了一个这样的树状路径结构？


### 实验方法（当前小节）


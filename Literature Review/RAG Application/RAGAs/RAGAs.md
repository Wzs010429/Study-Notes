# RAGAs: Automated Evaluation of Retrieval Augmented Generation


## 任务定义

提出自动化评价指标，包括文本检索的相似度评价，LLM忠实运用检索结果的可信度，生成内容的质量。避免评价结果过度依赖于人工评估指标从而提高了成本。

## 指标汇总


### Faithfulness


确保检索到的内容适合回答当前的问题，避免幻觉


刚开始没看明白，后来看明白了也没有很难，就是给定一个QA对，然后总结出来A中的所有句子。

例如，一个QA对中的A是由5句话构成的，我就把这5句话总结出来，但是不是按照标点拆分，而是用LLM去做更详细的切分。


### Answer Relevance


回答的答案与当前提问的问题是高度相关的


### Context Relevance

检索到的上下文应该是集中的，包含尽可能少的不相关的信息
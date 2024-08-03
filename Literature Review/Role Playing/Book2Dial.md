# Book2Dial: Generating Teacher-Student Interactions from Textbooks for Cost-Effective Development of Educational Chatbots

## 师生交互数据生成原理

针对一个知识文本，老师了解这个文本的全部，学生只了解部分（从整个知识文本中进行抽样）：

![](/Literature%20Review/Role%20Playing/Book2Dial/book2dailpic1.png)

> 遗留问题：这个文本是怎么传递的？有没有可能RAG？

- 老师的知识库就是把所有的文本全都喂过去，学生的可以进行采样：例如标题，摘要，元数据，总结这些可能在文章中直接出现的一个标志性符号的内容
- 老师会针对学生提出的问题进行引导性的回答，一般情况下不会是直接给出答案，但是也可能是到最后了给出来一个答案（这个需要去看一下具体的实验内容）
- 生成的数据文本是多轮次对话，每一轮当前对话都会携带了之前所有轮次的历史信息




## 教育学相关的7个评估指标

|指标名称|详细描述|实现原理|
|-|-|-|
|Answer Relevance|针对一个QA对（就是老师和学生的一问一答）来进行指标的评估，主要包含BERTScoreF1$(q_t, a_t)$，QuestEval$(q_t, a_t)$和Uptake$(q_t, a_t)$三个指标来实现|BERTScoreF1$(q_t, a_t)$：QA分别一个当参考句一个当预测句【from bert_score import score】；QuestEval$(q_t, a_t)$：也是计算语义相似性的【from questeval import QuestEval】；Uptake$(q_t, a_t)$：给定的一个QA对，计算点对点Jensen-Shannon Divergence (pJSD)，来评价老师针对学生问题回答的相关性|
|Coherence of the Dialogue|BERTScore F1 的两种用法|两个BERTScore F1的具体指标：一种是将当前轮次学生提出的问题作为预测句，然后将之前老师所有轮次的回答的答案作为参考句去计算相关性；另一种是将当前轮次学生提出的问题和上一轮次老师给出的答案作为一组去计算相关性|
|Informativeness|||
|Groundedness to the Textbook|||
|Answerability of the Questions|||
|Factual Consistency of the Answer|||
|Specificity of the Question|特异性评估，主要是人工评估|为了保障学生问出来的问题是和提供的知识文本相关的，而不是比较宽泛的问题，主要用人工评估，二元指标|
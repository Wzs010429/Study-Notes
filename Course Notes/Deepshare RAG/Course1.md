# 深度之眼 RAG 大模型课程 笔记


### Prompt 隐含假设


预训练语言模型包含丰富的知识，如何更好的利用它？


### Prompt Learning 提示学习 & Instructing Tuning 指示学习

Prompt Learning 对 Prompt的设计要求比较高，如果提示不够好那么其实模型是不能够有一个很好的输出和任务完成的。

Instructing Tuning其实是Fine-tuning加了一个prompt的前提条件，而且是针对多任务的一个泛化Tuning。它仍然在与训练语言模型的基础上，先在多个已知任务上进行微调（通过自然语言的格式），然后再应用在推理某个新任务上进行zero-shot。（最出名的就是FLAN）


COT & TOT


### 
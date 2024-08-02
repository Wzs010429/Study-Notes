# Book2Dial: Generating Teacher-Student Interactions from Textbooks for Cost-Effective Development of Educational Chatbots

## 教育学相关的7个评估指标

|指标名称|详细描述|实现原理|
|-|-|-|
|Answer Relevance|针对一个QA对（就是老师和学生的一问一答）来进行指标的评估，主要包含BERTScoreF1$(q_t, a_t)$，QuestEval$(q_t, a_t)$和Uptake$(q_t, a_t)$三个指标来实现|BERTScoreF1$(q_t, a_t)$：QA分别一个当参考句一个当预测句【from bert_score import score】；QuestEval$(q_t, a_t)$：也是计算语义相似性的【from questeval import QuestEval】；Uptake$(q_t, a_t)$：给定的一个QA对，计算点对点Jensen-Shannon Divergence (pJSD)，来评价老师针对学生问题回答的相关性|
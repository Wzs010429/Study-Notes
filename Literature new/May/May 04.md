# Autoregressive Models in Vision: A Survey


## Definition of Auito-regressive model



## Abstract

- 将视觉自回归模型的基本框架分为三个一般子类，包括基于像素的、基于令牌的和基于表示策略的尺度模型
- 探索自回归模型和其他生成模型之间的联系
- 提出了计算机视觉中自回归模型的多方面分类，包括图像生成、视频生成、3D生成和多模态生成


## Notes

- 3 distinct categories of visual autoregressive models defined by
their sequence representation strategies: **pixel-based, token-based, and scale-based** model


## Preliminary

- 序列表示。视觉数据首先被转换成离散元素的序列。这些元素可能对应于像素、图像块或从视觉内容派生的潜在代码，具体取决于特定的模型架构。这种转换允许将视觉数据框定为顺序建模问题，类似于自然语言处理中的文本生成


- 自回归序列建模。一旦视觉内容表示为有序序列，模型就会被训练为通过调节所有前面的元素来生成每个元素。从数学上讲，这表示为：


## 基于像素 pixel


看了一眼论文的时间 都太老了 所以暂时不投入尽力去研究

## 基于token

与直接对原始视觉数据进行操作的像素级模型不同，这种范式将图像或视频压缩和量化为一系列离散标记，从而可以更有效地处理高分辨率内容。



## 基于尺度 scale

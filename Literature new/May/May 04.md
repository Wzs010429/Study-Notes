# Problem Definition

设计一种融合自回归模型（Autoregressive Models, AR）与扩散模型（Diffusion Models, DM）的混合架构，实现以下目标：

- 稳定性：提升生成过程的可控性（如避免模式崩溃、梯度爆炸）和鲁棒性（对噪声输入或模糊文本的容忍度）。

- 可控性：增强对文本条件的细粒度响应能力（如精准修改局部区域、支持多模态输入）。

- 效率：平衡生成质量与计算成本（避免AR的长序列生成瓶颈或DM的迭代步数限制）。

关键研究问题
- 如何结合AR与DM的优势？

    - AR擅长序列建模和条件依赖（适合文本-图像对齐），DM擅长高质量生成和渐进细化。

- 如何设计混合架构的交互机制？

    - 是级联式（AR生成中间表示，DM细化图像）还是协同式（AR与DM交替迭代）？

- 如何解决训练与推理的兼容性？

    - 平衡离散（AR）与连续（DM）隐空间的表示差异，避免信息损失。

- 如何量化“稳定可控”？

    - 定义评估指标（如文本对齐度、生成多样性、局部编辑能力）。






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

这个暂时没有



### T2I 技术细节概览

#### Embedding

- language quantized autoencoders: Towards unsupervisedtext-image alignment
- Fluid: Scaling autoregressive text-to-image generative models with continuous tokens

#### Tokenizer

这仨带着看一眼就行

- Taming transformers for high-resolution image synthesi
- Scaling Autoregressive Models for Content-Rich Text-to-Image Generation
- Zero-shot text-to-image generation

#### Integration with Diffusion Models


- A diffusion-based autoregressive motion model for real-time text-driven motion control  这篇着重mark一下


#### Integration with Large Language Models


- Llm4gen: Leveraging semantic representation of llms for text-to-image generation
- Mars: Mixture of auto-regressive models for fine-grained text-to-image synthesis
- Lumina-mgpt: Illuminate flexible photorealistic text-to-image generation with multimodal generative pre-training

用自回归模型干掉扩散模型

Abstract：

1. 解决了当今的自回归模型包含encoder和decoder两个部分导致模型结构复杂的问题，简化模型架构
2. 灵活的高质量图片生成：提出了一个灵活的渐进式微调方法来不同精度下生成不同的离散标记（先粗分辨率，然后一点点提高精度）
3. 任务统一：将原本的不同形式的任务（多轮对话、视觉多轮理解、密集标记、文本到图像生成、文本到多视图生成、图像编辑和空间条件图像生成）是为统一的离散建模任务【构建多任务的通用mllM】
4. 不进行模型的随机初始化，使用Chameleon 7B和30B作为mGPT预训练模型Meta 【A100 32块！ 7天 只训练7B！】decoder-only

Methodology：
1. Tokenizer：将连续图像块从固定的密码本反转为离散的标记，同时降低空间维度。然后将量化的图像标记展平为一维序列，并与文本标记连接，形成统一建模的多模态标记序列

- Chameleon: Mixed-modal early-fusion foundation models

2. 微调环节：
将图片-文本对的分辨率定位在了三个阶段：512*512， 768*768和1024*102。



#### For Novel Generation

- Make-a-story: Visual memory conditioned consistent story generation
- Seed-story: Multimodal long story generation with large language model


#### Diffusion model only

- Scaling rectified flow transformers for high-resolution image synthesis
- Weak-to-strong training of diffusion transformer for 4k text-to-image generation
- Hunyuandit: A powerful multi-resolution diffusion transformer with fine-grained chinese understanding
- Kolors: Effective training of diffusion model for photorealistic text-to-image synthesis
- Lumina-next: Making lumina-t2x stronger and faster with next-dit.
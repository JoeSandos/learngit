# On the Shift Operator, Graph Frequency and Optimal Filtering in Graph Signal Processing

## first pass

### title

**keywords:** shift operator, graph frequency and optimal filtering, graph signal processing

[【图神经网络】图神经网络(GNN)学习笔记：图信号处理与图傅里叶变换](https://blog.csdn.net/ARPOSPF/article/details/122672970)

### abstract

- **问题背景:** 在图网络上定义信号平移操符很关键，涉及到图上的信号滤波、变换、预测操作

- **本文贡献：**
  - 定义了一套能量保持的图信号移位操作符，能和传统的信号处理有相同的属性
  - 否定了传统的基于邻接矩阵和Laplace矩阵的移位操作，因为这些操作改变了图信号的能量
  - 解耦了图结构的特征图和邻接矩阵/Laplace矩阵的特征矩阵
  - 证明了邻接矩阵的滤波符合LSI系统的定义，而非移位操作
  - 引入了图FIR和图IIR滤波器的显式形式
  - 定义了图上信号的自相关和互相关函数，使得能够获得图上最优滤波的解决方案（类似Wiener滤波、频域滤波、谱分析等）
  - 新的GSP框架让图上的信号分析能沿着图自身的由图时移流形定义的相关结构进行
  - 提供了一般图形上最优线性预测器问题的解决方案
  - 用仿真验证了最优LSI滤波器性能
- **关键词：** Graph signal processing, graph shift operator, graph Fourier transform, graph correlation function, graph spectral analysis, optimal filtering on graph

### Introduction

略，见上

## second pass

### A NEW SET OF SHIFT OPERATORS AND GRAPH FREQUENCY COMPONENTS

#### signals on graph

$ G=\{V,\mathbf{A}\} $, 其中V为顶点集合（N个），A为带权重的邻接矩阵，反映了顶点之间的关联。

> **graph signal定义**：从顶点集合到复数集合的一一映射
> - ![graph signal](images/15d859d44f6b2959d10d1c4b9b917b36db50d8a5c58f8f17851851d998bc01cd.png)  
> 
> 由此可得图信号向量$ \mathbf{x} $

> GSP中有两个基本的组成成分：顶点值表明的信号，以及顶点之间关联表明的信号关联结构

对于特殊情况如下图：
![周期信号的图表示](images/d795c8c53d26966bb45122f118bb129f5e0d24789ecd0b412e9eade8c0e6d2c6.png)  
有向环图，表示了**周期信号在图上的表示**，某个信号点对应图上的顶点，顶点之间的关联代表了信号的时移，满足$ x[n]=x[n+N] $

#### graph shift operator, information flow and filtering

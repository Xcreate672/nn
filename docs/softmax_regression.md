# Softmax回归

## 概述

Softmax回归（也称为多项逻辑回归）是逻辑回归在多分类问题上的推广，用于将输入分类到多个类别中的一个。

## 主要特点

- **多分类**：适用于类别数大于2的分类问题
- **概率输出**：输出属于各个类别的概率
- **互斥类别**：假设类别之间互斥

## 基本概念

### 1. Softmax函数

- 将实数向量映射为概率分布
- 公式：softmax(z_i) = exp(z_i) / Σexp(z_j)
- 输出概率之和为1

### 2. 决策边界

- 线性决策边界
- 通过权重矩阵W和偏置b定义

### 3. 损失函数

- 交叉熵损失
- 衡量预测概率与真实标签的差异

## 训练过程

### 1. 前向传播

- 计算线性变换：z = Wx + b
- 应用softmax函数得到概率

### 2. 计算损失

- 使用交叉熵损失函数
- 衡量预测与真实标签的差异

### 3. 反向传播

- 计算梯度
- 更新权重和偏置

## 与逻辑回归的关系

- 逻辑回归是Softmax回归的特例（类别数=2）
- Softmax回归是逻辑回归的推广
- 两者都使用线性变换和softmax函数

## 应用领域

- 图像分类
- 文本分类
- 手写数字识别
- 情感分析
- 
## 代码示例

使用 PyTorch 实现 Softmax 回归：

```python
import torch
import torch.nn as nn

class SoftmaxRegression(nn.Module):
    """Softmax回归（多分类）"""
    def __init__(self, input_dim, num_classes):
        super(SoftmaxRegression, self).__init__()
        self.linear = nn.Linear(input_dim, num_classes)

    def forward(self, x):
        return self.linear(x)  # CrossEntropyLoss内部已包含softmax

# 创建模型，例如10分类
model = SoftmaxRegression(input_dim=784, num_classes=10)
criterion = nn.CrossEntropyLoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.01)
```

## 在 Carla 中的应用

Softmax 回归可用于 Carla 场景中的多类别分类任务：

- **交通标识分类**：将摄像头图像分类为限速、禁止通行、停车等多种标识
- **路况分类**：将当前路况分类为直行、左转、右转等驾驶决策
- **天气分类**：对场景天气进行晴天、雨天、雾天等多类别判断

## 运行环境

- Python 3.7+
- PyTorch 1.8+

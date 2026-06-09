# 简单神经网络

## 概述

简单神经网络是深度学习的基础，通常指包含一个或少数几个隐藏层的前馈神经网络，是理解复杂神经网络架构的起点。

## 主要特点

- **前馈结构**：信息从输入层单向流向输出层
- **全连接**：相邻层的神经元全部连接
- **非线性激活**：使用激活函数引入非线性

## 基本结构

### 1. 输入层 (Input Layer)

- 接收原始特征数据
- 节点数量等于特征维度

### 2. 隐藏层 (Hidden Layer)

- 提取数据特征
- 可以有多个隐藏层
- 节点数量影响模型容量

### 3. 输出层 (Output Layer)

- 产生最终预测结果
- 节点数量取决于任务类型

## 激活函数

### 常用激活函数

- **Sigmoid**：将输出映射到(0,1)区间
- **Tanh**：将输出映射到(-1,1)区间
- **ReLU**：修正线性单元，max(0,x)

## 训练过程

### 1. 前向传播

- 计算各层输出
- 得到预测结果

### 2. 计算损失

- 使用损失函数衡量预测误差
- 常用均方误差、交叉熵等

### 3. 反向传播

- 计算梯度
- 更新权重和偏置

## 应用领域

- 分类问题
- 回归问题
- 模式识别
- 函数逼近
- 
## 代码示例

使用 PyTorch 实现一个简单的两层神经网络：

```python
import torch
import torch.nn as nn

class SimpleNN(nn.Module):
    """简单两层全连接神经网络"""
    def __init__(self, input_dim, hidden_dim, output_dim):
        super(SimpleNN, self).__init__()
        self.net = nn.Sequential(
            nn.Linear(input_dim, hidden_dim),
            nn.ReLU(),
            nn.Linear(hidden_dim, output_dim)
        )

    def forward(self, x):
        return self.net(x)

# 创建模型
model = SimpleNN(input_dim=2, hidden_dim=16, output_dim=1)
print(model)
```

## 运行环境

- Python 3.7+
- PyTorch 1.8+

## 运行步骤

```bash
cd src/chap04_simple_nn
python main.py
```

## 与其他模型的对比

| 模型 | 特点 | 适用场景 |
|------|-----|---------|
| 线性回归 | 无隐藏层，只能线性分类 | 线性可分数据 |
| 简单神经网络 | 一到两个隐藏层 | 非线性简单任务 |
| CNN | 卷积结构，擅长图像 | 图像识别 |

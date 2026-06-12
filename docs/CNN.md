# 卷积神经网络 (CNN)

## 概述

卷积神经网络（Convolutional Neural Network, CNN）是一种专门用于处理具有网格结构数据的深度学习架构，特别适用于图像识别和计算机视觉任务。

## 主要特点

- **局部连接**：每个神经元只与输入数据的局部区域连接
- **权重共享**：同一卷积核在整个输入上共享权重
- **池化操作**：通过下采样减少数据维度，提高计算效率

## 基本结构

### 1. 卷积层 (Convolutional Layer)

- 使用卷积核提取局部特征
- 通过滑动窗口操作生成特征图

### 2. 激活函数 (Activation Function)

- 常用ReLU、Sigmoid、Tanh等
- 引入非线性变换

### 3. 池化层 (Pooling Layer)

- 最大池化、平均池化等
- 降低特征维度，增强平移不变性

### 4. 全连接层 (Fully Connected Layer)

- 将特征图展平后进行分类或回归

## 应用领域

- 图像分类
- 目标检测
- 图像分割
- 人脸识别
- 医学影像分析
  
## 代码示例

使用 PyTorch 定义一个基础 CNN 网络：

```python
import torch.nn as nn

class BasicCNN(nn.Module):
    """基础卷积神经网络"""
    def __init__(self, num_classes=10):
        super(BasicCNN, self).__init__()
        self.features = nn.Sequential(
            nn.Conv2d(3, 16, kernel_size=3, padding=1),
            nn.ReLU(),
            nn.MaxPool2d(2, 2),
            nn.Conv2d(16, 32, kernel_size=3, padding=1),
            nn.ReLU(),
            nn.MaxPool2d(2, 2),
        )
        self.classifier = nn.Linear(32 * 8 * 8, num_classes)

    def forward(self, x):
        x = self.features(x)
        x = x.view(x.size(0), -1)
        return self.classifier(x)
```

## 在 Carla 中的应用

- **交通标识识别**：识别限速、停车等标识
- **车道线检测**：提取图像中的车道线特征
- **障碍物检测**：识别前方行人、车辆等障碍物

## 参考资料

- [PyTorch Conv2d 文档](https://pytorch.org/docs/stable/generated/torch.nn.Conv2d.html)

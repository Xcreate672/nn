# 热身示例

## 模块简介

本模块用于帮助初学者熟悉 NumPy 的基本操作，包括数组创建、切片、索引、矩阵运算以及简单绘图等内容。

## 代码位置

- 源码文件：`src/chap01_warmup/numpy_tutorial.py`

## 学习内容

本示例主要包括以下内容：

- 一维数组与二维数组的创建
- 矩阵形状与元素访问
- 数组切片与高级索引
- 常见数学运算
- NumPy 与 Matplotlib 基本绘图

## 运行方式

在项目根目录下执行：

```bash
python src/chap01_warmup/numpy_tutorial.py
```

## 说明

运行后会在终端输出各小题结果，并绘制简单函数图像。

## 各练习详细说明

### 1. 数组创建与基本操作

```python
import numpy as np

# 创建一维数组
a = np.array([1, 2, 3, 4, 5])
print(a.shape)   # (5,)
print(a.dtype)   # int64
```

### 2. 矩阵运算

```python
# 矩阵乘法
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])
C = np.dot(A, B)
print(C)  # [[19 22], [43 50]]
```

### 3. 数组切片与索引

```python
a = np.arange(10)
print(a[2:5])    # [2 3 4]
print(a[::2])    # [0 2 4 6 8]
```

### 4. 简单绘图

运行后会弹出如下图形：
- x 轴：0 到 2π
- y 轴：sin(x) 函数曲线

## 常见问题

- **导入报错**：请先执行 `pip install numpy matplotlib`
- **图形不显示**：检查是否安装了图形界面，或将 `plt.show()` 改为 `plt.savefig('output.png')`


## 完整代码

[完整代码](https://github.com/OpenHUTB/nn/blob/main/src/chap01_warmup/numpy_tutorial.py)

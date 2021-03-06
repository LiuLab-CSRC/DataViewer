## DataViewer 使用说明
[English](https://github.com/estonshi/DataViewer/blob/master/README-en.md)

### 简介
这是一个数据可视化工具，主要为单颗粒散射的数据分析开发。

1. 2dViewer : 二维散射数据的展示，以及一些分析
2. maskMaker : 二维图像遮罩的制作
3. 3dViewer : 三维数据的展示

### 安装环境
本程序基于Anaconda环境开发。

1. 安装Anaconda 3；
2. 运行“make.sh”脚本（只支持Linux和苹果系统），或者使用包内提供的“environment.yaml”文件自行配置环境。

### 使用

1. 二维数据展示

```bash
python ./2dViewer/viewer.py
```

2. 制作二维图像遮罩

```bash
python ./2dViewer/maskMaker.py
```

3. 三维数据展示

```bash
python ./3dViewer/viewer.py
```

---

### 使用文档

#### （1）3dViewer

首先，从左侧文件选择器选择想要展示的数据，再点击下方“Import Selected File”按钮加载即可。用户可以在右侧下方控制栏中选择多种绘图模式（名为“Plot”的下拉菜单）。

**【动图制作器】**

点击“Rotate and Movie”按钮（右侧下方控制栏内），可以控制绘图场景的旋转并且录制动图。

* 制作动图 : 在弹出窗口中设置总时长并点击“Make Movie”按钮即可。在弹窗左下角可以查看制作进度。
* 旋转 : 点击“Rotate”按钮，仅对绘图场景进行旋转。

**【数据格式】**

* 目前支持“.npy”（Numpy数据），“.mat”（Matlab数据），“.bin”（二进制），".h5"（HDF5格式）文件。

* 标量绘图 : 绘制标量数据，数据矩阵应为**三维**。
	* 矩阵形状=（Nx，Ny，Nz）
* 向量绘图 : 绘制向量数据，数据矩阵应为**二维**，6行N列。
	* 6行分别为（X坐标，Y坐标，Z坐标，X方向速度，Y方向速度，Z方向速度）
	* N列，即一共N个数据点
* 离散点绘图 : 对三维空间的离散点进行绘制，可带强度值，数据矩阵应为**二维**，3或4行，N列。
	* 4行分别为（X坐标，Y坐标，Z坐标，强度）
	* N列，即一共N个数据点

#### （2）2dViewer

二维数据展示程序使用简单，直接将HDF5文件、Numpy数据文件、Matlab数据文件或TIF文件拖拽到右侧文件树下，双击相应数据即可。

在“Parameter”选项卡中可调节各种显示参数。

#### （3）2D 数据遮罩

程序提供形状的三种遮罩工具：

* 圆遮罩工具
* 矩形遮罩工具
* 多边形遮罩工具

通过调节这些工具的大小和位置，可以组合出任意的遮罩形状。

* **右键单击**遮罩工具 : 将该工具圈定的范围纳入当前数据遮罩
* **左键双击**遮罩工具 : 将该工具圈定的范围从当前数据遮罩中除去
* **右键单击**文件树中的遮罩文件 : 显示下拉菜单，可将选中文件（必须二维）设置为当前遮罩，或加入到当前遮罩中去。

同样，“Parameter”选项卡提供了很多重要的参数设置，其中“Mask Good”和“Mask Bad”分别定义了读写遮罩文件时，无遮罩部分和被遮罩部分的数据值。

# yolov5环境配置

[TOC]

## 配置

![image-20250111135828878](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111135828878.png)

## 所需环境

**Anaconda（Python）**

**CUDA (GPU加速)**

**requirements.txt (yolov5)**

## 前期准备

![image-20250111140716924](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111140716924.png)

根据requirements.txt文件，共需准备环境如上，可以直接通过引入该文件来引入所需环境（后面说）；

但其中Pytorch文件较大可能呢没有办法下完，或者出现各种问题，故可以从外部引入；

（后面再进行操作）外部引入后在requirements.txt中注释掉，防止额外或错误引入，如下

![image-20250111141222154](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111141222154.png)

综上，除anaconda作为平台外（其作用为能够建立多种独立Python环境），总共需要引入的环境及他们最基本的兼容问题如下：

（其中requirements.txt无需过多考虑兼容问题）

![image-20250111142050155](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111142050155.png)

明确一点，作为一个纯小白，可以尝试放弃一些最新版本和明确告诉你还在测试的版本，来减少不必要的麻烦

## 环境选择

#### CUDA选择

由上图可知，CUDA需要考虑与电脑的兼容性和与pytorch的兼容性

首先查看电脑是否已经安装CUDA：打开cmd输入如下命令

`nvcc --version`

若出现如下结果则证明已安装（不一定兼容，后面讲）：

![image-20250111143436429](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111143436429.png)

若结果显示不是内部或外部命令则说明未安装

输入如下命令查看电脑支持的CUDA：

`nvidia-smi`

![image-20250111144514657](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111144514657.png)

进入[CUDA](https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html)官网查看兼容型号

![image-20250111144625582](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111144625582.png)

可见，电脑支持的CUDA版本最高为12.6.1，及可选择低于12.6.1的版本

#### pytorch选择

我们已知pytorch需要考虑与CUDA和Python的兼容性

进入[pytorch官网](https://pytorch.org/)查看兼容性：

![image-20250111145535913](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111145535913.png)

其中conda和pip都可以，理论上有些许区别，我个人尝试都能用（可以哪个快用哪个）

由NOTE可知，支持Python 3.9及更高，但最高支持CUDA 12.4，我个人选择了较低版本12.1

## 环境配置

#### 1.CUDA

进入[CUDA官网](https://developer.nvidia.com/cuda-toolkit-archive)，选择合适版本

![image-20250111151040734](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111151040734.png)

下载并运行安装程序

![image-20250111151155112](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111151155112.png)

![image-20250111151234759](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111151234759.png)

后面懒得写了，可以参考这篇文章（https://blog.csdn.net/m0_53883779/article/details/135701971）

#### 2.Anaconda

懒得写了，可以参考这篇文章（https://blog.csdn.net/Python_trys/article/details/141715978）

其中这张图片中红色那条在配置环境变量，一定要勾选

![img](https://i-blog.csdnimg.cn/direct/3edc5e3c196d4540ada0cc675650860b.png#pic_center)

Anaconda默认下载源为国外源，如果使用国内网则速度很慢且容易中断。因此建议设置国内源为默认下载源。推荐使用清华镜像源

打开cmd，输入以下命令

`conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main`
`conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free`
`conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r`
`conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro`
`conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2`

`conda config --set show_channel_urls yes #终端显示包从哪个channel下载，以及下载地址是什么`

#### 3.yolov5 （requirements.txt）

进入github仓库（科学上网）（https://github.com/ultralytics/yolov5）

下载并解压

![image-20250111160646692](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111160646692.png)

可以看到所需文件

![image-20250111160751917](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111160751917.png)

打开后注释掉以下内容 (直接导入torch)

![image-20250111160932761](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111160932761.png)

#### 4.pytorch及requirements.txt

打开cmd，使用如下形式代码创建一个环境：

`conda create -n 名字 python=3.X`

其中名字随便取，记得住就行；X替换为对应版本

![image-20250111153428631](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111153428631.png)

出现以上结果输入y并回车

![image-20250111154452929](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111154452929.png)

安装结束并启动环境，即输入`conda activate 环境名`，出现以下结果

![image-20250111154656540](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111154656540.png)

输入`conda list`查看已导入的库

![image-20250111154854198](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111154854198.png)

输入该命令

![image-20250111155149889](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111155149889.png)

输入y并回车

![image-20250111155242379](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111155242379.png)

完成后再次输入`conda list`，出现如下三个

![image-20250111155622554](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111155622554.png)

也可打开Python（输入`python`)

![image-20250111155730977](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111155730977.png)

输入`import torch`检验是否完成配置

输入`print(torch.cuda.is_available())`检验是否兼容CUDA，若返回True则证明兼容

输入`exit()`退出python （不退出创建的环境）

输入`pip install -r D:\yolov5-master\requirements.txt`，即requirements.txt文件的绝对地址

![image-20250111161451210](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111161451210.png)

完成

#### 5.补充 vscode配置

打开yolov5对应文件夹

快捷键Ctrl+Shift+P，输入 Python:Select Interpret，选择对应环境

![image-20250111161918354](C:\Users\wangr\AppData\Roaming\Typora\typora-user-images\image-20250111161918354.png)

## 补充说明

因为完成配置后重新编写记录，期间话费时间较长，可能存在一些其他问题，建议查CSDN，绝大部分都能解决。
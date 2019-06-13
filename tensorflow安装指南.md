<br/>
# <center>tensorflow安装总结<center>
<br>记录在window下安装tensorflow遇到的一些问题及解决方法。另外第一次用markdown记录学习心得，纪念一下。<br>
官网操作基本不可用，问题不给解决，因此搜集了一些网上的解决方法。
最好的操作感觉是在anaconda环境下进行安装，各个管理包互相隔离，在pycharm下导入即可用。

引用一些对anaconda的描述。     
<br>Anaconda是一个免费开源的Python和R语言的发行版本，用于计算科学（数据科学、机器学习、大数据处理和预测分析），Anaconda致力于简化包管理和部署。Anaconda的包使用软件包管理系统Conda进行管理。
<br>可以使用已经包含在Anaconda中的命令conda install或者pip install从Anaconda仓库中安装开源软件包。Pip提供了Conda大部分功能，并且大多数情况下两个可以同时使用。可以使用conda build命令构建自定义包，然后通过上传到Anaconda Cloud、PyPI或其他仓库来分享给其他人。<br>

<br>本机环境：
<br>python3.7.4
<br>window 10
<br>Anaconda 3

自动安装，
><br>1.运行 开始菜单->Anaconda3—>Anaconda Prompt ，在弹出的命令窗口输入：
>`conda list`
>即可看到已经安装了numpy、sympy等常用的包。

><br>2、同样在Anaconda Prompt中利用Anaconda创建一个python3.5的环境，环境名称为tensorflow ，输入下面命令：
`conda create -n tensorflow python=3.5`
<br>这样就创建了一个名为tensorflow的python3.5的环境。运行 开始菜单->Anaconda3—>Anaconda Navigator，点击左侧的Environments，就可以看到。

><br>3、在Anaconda Prompt中启动tensorflow环境：
>`activate tensorflow`
  //关闭命令为：deactivate

><br>4、安装TensorFlow：
>//CPU版本
<br>`pip install --upgrade --ignore-installed tensorflow`
<br>//GPU版本，根据自己需要选择版本号，没有的话会安装最新的版本
<br>`pip install --upgrade --ignore-installed tensorflow-gpu==1.8.0`

<br>等待一会后，tensorflow 就安装好了。 
这种方法仅仅是安装TensorFlow的包，并没有安装相关的依赖包。 
如果缺少相关的依赖包话，**推荐还是用conda安装：**
<br>//CPU版本，同样，后面可以跟版本号
<br>conda install tensorflow
<br>//GPU版本
conda install tesorflow-gpu
<br>版本号自行选择

<br>5、测试tensorflow            
在Anaconda Prompt中启动tensorflow环境，并进入python环境。

<br>测试代码如下:
<br>`import tensorflow as tf`
<br>`print(tf.__version__)`

###一些问题：
<br>输入:`conda list`
       
可以查看已安装库
<br>`conda info --envs`
<br>查看已安装环境

###出现如下代码错误：
<br>*
```
<p>
from PIL import Image
Traceback (most recent call last):
  File "<ipython-input-12-0f6709e38f49>", line 1, in <module>
    from PIL import Image

  File "d:\ProgramData\Anaconda3\lib\site-packages\PIL\Image.py", line 58, in <module>
    from . import _imaging as core

ImportError: DLL load failed: 找不到指定的模块。
<p>
```
<br>1.重新install该模块
<br>2. 该环境支持python32位而不是64位，重装32位python至该环境，但不会影响其他环境。

<br>*1.0使用TensorFlow模块时，弹出错误`Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX AVX2`
+	 忽略这个警告，不看它！
<br>`import os  `
<br>`os.environ["TF_CPP_MIN_LOG_LEVEL"]='1'` # 这是默认的显示等级，显示所有信息  
<br>`os.environ["TF_CPP_MIN_LOG_LEVEL"]='2'` # 只显示 warning 和 Error   
<br>`os.environ["TF_CPP_MIN_LOG_LEVEL"]='3'` # 只显示 Error

<br>选择第二个。
<br>+换成支持cpu用AVX2编译的TensorFlow版本。
<br>去github下载正确的tf版本，[Windows](https://github.com/fo40225/tensorflow-windows-wheel)点这里下载。
<br>对应的path在上边的找到对应的.whl下载即可。

然后安装：
<br>`pip install tensorflow-1.6.0-cp36-cp36m-win_amd64.whl`
<br>此方法并没有尝试。
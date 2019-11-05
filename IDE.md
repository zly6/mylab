# Jupyter概述
## 安装工具
- pip: python的包管理工具，提供单一稳定的包仓库
- conda: 包管理工具之外，还是环境管理工具
    - 包获取方式是通过channel（仓库，多种选择）获取，其中，conda-forge是社区支持的channel，更可靠
    - 每个环境中，可以进行个性化配置，而环境之间互不影响；使用场景：同时使用不同版本不同工具的环境，想尝试更新的软件包但仍想留在原软件上开发。
    
## 环境管理
环境的根目录：下载的包在anaconda安装根目录下的pkgs中，环境信息则在envs下（奇怪，怎么打开文件后，没看到什么列表呢）
基础环境：`base`，Anaconda安装目录下。
### 环境配置
两种创建方式(conda create --help)：
- 使用name唯一标识环境：`conda create --name wind packages=version`，此时环境文件在conda安装根目录下的envs文件夹下。
- 使用path唯一标识环境：`conda create --prefix F:\zly\work\jupyter\jupyterLab packages=version`，F:\zly\work\jupyter\jupyterLab就成为该环境的唯一标识，调用时也用它。

进入环境后，增加包：`conda install package`，不进入环境也可以：`conda install -n envName package`

**如果安装的包有依赖，在安装依赖前会咨询是否继续安装依赖，需要回复yes才能继续任务。对此，可在.condarc中增加一条配置：always_yes: true**

移除包：`conda remove -n envName package`

查看环境中已安装的包：`conda list`

查看conda的配置信息（存储在.condarc文件中，内容包括channels,proxy server,envs directories）可用如下指令获取：`conda info`

增加channel：`conda config --add channels`，也可以对某个环境个性化设计配置，可将.condarc放在conda安装目录下的envs下该环境文件名下。

### 启动环境：
- 查看已创建环境列表：`conda env list`
- 启动环境：`conda activate F:\zly\work\jupyter\lab1`
- 启动jupyterLab：`jupyter lab --watch`

# 实例演示
## 根据JupyterLab上的天文图像案例
- 下载anaconda3 5.2。 电脑（系统Win10）之前便安装了Anaconda3, 5.3.0版本，结果在生成环境时报错：无法定位程序输入点 。。。动态链接库，类似的问题可见[该页面](https://blog.csdn.net/Msjiangmei/article/details/100925060)。重装 Anaconda3 5.2.0版本，
- 打开anaconda prompt
- conda update conda：因为例子中的代码都是按照4.6以上版本写的，（4.6版本18年的，而jupyterlab是19年年初推出的。）
- conda create -n jupyterlab-ext --override-channels --strict-channel-priority（上述两条用来严格按照channel优先级搜索包） -c conda-forge -c anaconda（列出两个channel，优先级前高后低） jupyterlab cookiecutter nodejs git （需要安装的包，实际上，为了安装这些包，还需要安装一些依赖，会在窗口中显示出来）
- 然后，依次按照引导，修改配置，增加扩展，最终，在command工具中输入Random 

## 添加镜像
### 常用的官方镜像
```
conda config --add channels bioconda
conda config --add channels conda-forge
```
### 清华镜像
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
```
## 版本控制与搬移
### github版本同步
```
git remote add orgin https://github.com/zly6/jupyter-ext.git
git commit -m "Second commit"
git push -u origin master
```

### 环境搬移
1. 进入目标环境: `conda activate -n myenv`
2. 生成yml文件:`conda env export > environment.yml`
3. 利用yml文件生成环境：`conda env create -f environment.yml`

## 功能扩展（jupyter extension）
1. JupyterLab 的插件是 npm 安装包。所以按照 JupyterLab 的插件，需要提前按照好 Node.js。
2. 安装插件
    - 方法一：通过开启 Extension Manager （菜单栏Settings-Advanced Settings Editor）来安装和管理插件
        - 设置“enabled”: true
        - 即可在走侧边栏中看到插件选项卡，可以查看已经按照的插件和探索其他未安装的插件。
        - 要令扩展生效，需要重新启动环境与jupyterLab
    - 方法二：通过执行命令的方式安装。
    
## 增加kernel
支持多种语言的拓展，直接创建该类型文件并运行调试。
jupyter Kernel[目录](https://github.com/jupyter/jupyter/wiki/Jupyter-kernels)
例如：
- matlab: `pip install matlab_kernel`, 然后就可以创建matlab文件了。

同时，还支持在同一文档内[使用多种语言](https://vatlab.github.io/blog/post/sos-notebook/)。

**问题**：不知为何，简单的代码执行的也特别慢。
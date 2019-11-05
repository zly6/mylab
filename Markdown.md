# Markdown使用
## 字体
*斜体*

**粗体**

***粗斜体***

~~删除线~~

<u>下划线</u>

**脚本有问题** 创建脚本[^footnote]

[^footnote]：天天学习

- 第一列表
    - 第二级列表（前面加四个空格）

## 区块

> 区块引用
>> 第二级

代码或函数可用反引号'将其包起来： `printf`函数，而代码区块可通过前面加四个空格或一个tab键或者前后加三个反引号

```
print("Hi, new world")
hihihi
```  
## 链接

[链接](www.baidu.com)

链接也可以用变量来代替，文档末尾附带变量地址：
这个链接用 1 作为网址变量 [Google][1]
这个链接用 runoob 作为网址变量 [Runoob][runoob]
然后在文档的结尾为变量赋值（网址）

[1]: http://www.google.com/
[runoob]: http://www.runoob.com/

## 表格

| 左对齐 | 右对齐 | 居中对齐 |
| :-----| ----: | :----: |
| 单元格 | 单元格 | 单元格 |
| 单元格 | 单元格 | 单元格 |

## 公式
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} 
\mathbf{i} & \mathbf{j} & \mathbf{k} \\
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \\
\end{vmatrix}
$$
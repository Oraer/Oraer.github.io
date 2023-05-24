> 关于rosdep update 命令 更新失败 ERROR: unable to loadsource或者 ERROR: unable to process source 或者 timeout

关于 rosdep update 报错折磨我将近三个小时这件事。

然后就去尝试运行  rosdep update

```
rosdep update
```

 但是在运行这条命令是却遇到了错误

```shell
ERROR: unable to load source [https://raw.githubusercontent.com/......]......
```

```shell
ERROR: unable to process source [https://raw.githubusercontent.com/......]......
```

我也根据文章2中的方法修改 host 地址，但是没有起作用。

文章中说多尝试几遍，然后我用热点尝试将近3个小时，搞得我又都想重新装系统了



直到我找到了这篇文章1

>  ROS rosdep update更新失败（简单解决）

## 解决方案



直接安装

```shell
sudo pip install rosdepc
```

如果没有pip可以使用pip3

如果还没有的话：

```python
sudo apt-get install python3-pip 

sudo pip install rosdepc
```



最后运行：

```
rosdepc update
```



注：文章1作者也是使用了文章2作者的解决方法

>文章1：[ROS rosdep update更新失败（简单解决）](https://blog.csdn.net/weixin_53660567/article/details/120607176?spm=1001.2014.3001.5501)
>
>文章2：[本文之后，世上再无rosdep更新失败问题！如果有....小鱼就...](https://mp.weixin.qq.com/s/VGs8oWdhHH6XsHcx21lN4Q)
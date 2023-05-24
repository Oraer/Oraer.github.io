> ROS rosrun、launch命令无法TAB自动补全功能包

## 问题

关于我将虚拟机扩容后也可能是其他原因（装了中文语言包、或者使无意间更新了依赖），我运行 rosrun命令甚至没有办法TAB补全turtlesim等小海龟命令这件事。

##  闲扯

第一次扩容后遇到这件事时，我捣鼓了好一会，在网上找资料每也有找到，然后以为要完成老师布置的作业然后就重新装镜像了。

然后第二次遇到这件事也就是这次的时候，我决定和这个问题杠到底，一定要解决这个问题。

我严重怀疑时老师给的镜像及配置文件有问题。



## 正文开始

但是像 roscore，rosrun，rosluanch等基本ROS操作命令能够TAB补全

但是我如果手动吧命令敲全的话是能够运行的

```shell
rosrun turtlesim turtlesim_node
```

rosluanch也是如此，但就是无法使用TAB命令自动补全。

以下是我的解决思路，如果想直接知道，建议直接跳到解决方案。



## 我的解决思路

我一开始以为使我吧ROS环境变量弄没了

使用  echo $ROS_PACKAGE_PATH   查看，发现也没有问题

```shell
echo $ROS_PACKAGE_PATH
```

然后我去查找去搜索，却只发现了类似的问题 

在文章一中的博主是这样做的

>  [ROS] roslaunch命令Tab无法自动补全

文章中说需要   rospack profile  一下

```
rospack profile
```

我也试了一下，但是不起作用



还有一个文章二中博主的解决方法是

> 【ROS入坑】古月居第19讲—Roslaunch无法补全功能包的解决方法

在终端中输入以下命令   rospack list

```shell
rospack list
```

我还是试了一下，但是不起作用



后来一想可能是rosdep依赖库出了问题

然后尝试了文章三博主的方法

> ROS Melodic 安装必成功流程+避坑指南（超详细）


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

关于如何解决这个 rosdep update 问题，我会在另一篇文章中写出。

以下是连接

> [关于rosdep update 命令 更新失败 ERROR unable to loadsource或者 ERROR unable to process source 或者 timeout](https://blog.csdn.net/m0_54056489/article/details/127055224?spm=1001.2014.3001.5502)



后来找到了文章四

> 无法补全ros命令

根据博主的方法，在终端中输入   sudo apt-get install bash-completion rosbash

```
sudo apt-get install bash-completion rosbash
```

在输入完这条命令重启后，roslanunch 命令能够补全功能包了，但是 rosrun 命令还是不能够补全功能包



**然后就到了我们的解决方案**

到了文章五的博主出现

>  Command ‘rosrun‘ not found，rosrun找不到的问题

我根据我的ROS版本修改了一下命令，然后完美解决问题。



## 解决方案

在运行完这条命令后需要重启才能生效：

```
sudo apt install ros-melodic-rosbash
```

中间的melodic是ros版本号，可以通过roscore查看

不同版本的ROS需要根据版本替换

![image-20220923211026536](https://cdn.jsdelivr.net/gh/Oraer/blogimg/img/image-20220923211026536.png)





参考文章

>文章1：[挨打日记ROSroslaunch命令Tab无法自动补全](https://blog.csdn.net/m0_51495658/article/details/115717577)
>
>文章2：[【ROS入坑】古月居第19讲—Roslaunch无法补全功能包的解决方法](https://blog.csdn.net/spaceshield/article/details/121339930)
>
>文章3：[ROS Melodic 安装必成功流程+避坑指南（超详细）](https://blog.csdn.net/hxj0323/article/details/121215992)
>
>文章4：[无法补全ros命令](https://blog.csdn.net/aozhipujian10997/article/details/86009322)
>
>文章5：[Command ‘rosrun‘ not found，rosrun找不到的问题](https://blog.csdn.net/num8owl/article/details/108689843)
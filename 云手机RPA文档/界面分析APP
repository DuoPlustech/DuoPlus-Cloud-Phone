为了方便编辑RPA流程，桌面新增了应用DumpElement。该应用主要用于提取界面中元素的信息，默认情况下。该APP是隐藏的。在使用时可以主动显示该应用。

## 使用介绍

该工具主要针对当前界面中的可点击元素进行分析，提取出元素的各类信息，在RPA中填写对应的信息来找到该元素进行操作。首先从开发者工具中显示该应用

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd32551f91.png)

然后开启显示该工具

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd389c6593.png)

在桌面上找到该工具图标如下

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd3ba272bb.png)

该应用的界面

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd3e9c3547.png)

右上角的按钮为缩小按钮，点击后可将应用缩小为悬浮球，再次点击会还原成原界面

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/f92e5cc0118b2ec4a09e3bf9021a7245.png)

主界面中三个按钮分别是**分析界面**、**清空界面**、**关闭应用**。分析的效果如下

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd42db4133.png)


点击绿框内的元素则会展示该元素的详细信息

> 需要注意package是当前应用的包名，如当前页面是桌面，就是Luncher的包名

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/70a5c8da146777425a05db89471d2d1c.png)

点击选中信息的值，则会将其复制到粘贴板。

## 实践使用

为了更好的理解，下面以实际场景为例。如刚刚的元素详细信息为Settings图标。在RPA中想要点击该图标有几种方式

### 1.包名
如打开设置页面后，使用该工具分析界面，可以看到该应用的包名，点击后自动复制包名

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/15ae2e6cc8179d7ceda8df1e181bf4fc.png)

然后RPA中使用打开应用。输入包名，即可运行该应用

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd521ea848.png)


### 2.元素选择

在RPA中所有和元素获取相关的操作中，都可以通过fullid、class、text、desc几个属性来找到对应的元素

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd63c62021.png)

在一些特殊的界面中，如果通过上面的几个属性无法定位到单个元素，匹配到多个结果时。则可以通过元素排序来指定要第几个元素。

### 3.无障碍模式

有一些特殊的场景，需要使用无障碍模式才能正常获取到元素的情况，可以通过下面的功能快捷的切换

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd6b449392.png)

修改为使用无障碍模式

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd70279cf7.png)

配置哪台设备采用无障碍模式

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd739b1cf9.png)

再次打开界面分析工具，可以看到分析按钮的图标变化了，说明当前采取了无障碍的界面分析方式

![](https://resource-wangsu.helplook.net/docker_production/wkpufm/article/jhV5aaPS/694cd7c1de693.png)

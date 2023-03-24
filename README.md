## 基于Wi-Fi的室内定位系统
[![](https://img.shields.io/badge/video-1.0-green)](https://b23.tv/d6bHme)

### ↑↑↑ 功能演示
​ Android室内定位，包括功能：数据采集、WiFi+PDR定位、路径规划
### 详细代码及论文请联系q：3192196841

###  一、概要

​        室内定位技术是一种在室内无法使用精确的GPS服务所衍生出来的技术。由于传统的卫星信号到达地面时，信号强度变弱，加上建筑物、室内复杂环境的影响，诸如GPS或者北斗等定位系统不能提供精确的位置服务。然而，人们对于室内定位的需求却日益增加，所以室内定位系统的研究是解决移动服务最后一米的机会。常见的无线定位技术有：WiFi、蓝牙、红外线、超宽带、RFID、ZigBee和超声波等。行人航位推算是通过测量目标的运动方向和运动速度来对目标当前位置进行估计的一种方法。这种方法来源于航海过程中，船员要知道自己目前所在的位置，船员通过起始点进行推算，使用罗盘等工具记录运动的方向和运动的速度，同时也通过标志建筑的纠正，来确定自己的当前位置。本系统就是采用基于Android平台的WiFi指纹技术和行人航位推算技术（PDR）设计实现的。通过WiFi室内定位系统获得目标的起始位置，之后通过PDR技术估算出现有位置，通过这种方式，得到更加精确的位置，弥补传统定位系统的不足。

### 二、K近邻算法介绍

​       K近邻算法是一种分类算法，它首先获得一个样本训练集，样本训练集中的每一组数据都有自己的标签，通过当前点的特征与样本训练集中数据对应特征进行比较，得到最相似的数据标签，最相似数据一般选用前K个，这就是K近邻算法中K的来源，最后选择相似数据中标签概率最大的，作为新数据的标签。其中衡量相似的标准常用的有：曼哈顿距离、欧氏距离等。

![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200520232130.png)

![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200520232255.png)

公式中i表示标签，n表示AP的个数

### 三、行人航位推算法介绍

​        行人航位推算是通过测量目标的运动方向和运动速度来对目标当前位置进行估计的一种方法。这种方法来源于航海过程中，船员要知道自己目前所在的位置，船员通过起始点进行推算，使用罗盘等工具记录运动的方向和运动的速度，同时也通过标志建筑的纠正，来确定自己的当前位置。行人航位推算是通过测量目标的运动方向和运动速度来对目标当前位置进行估计的一种方法。这种方法来源于航海过程中，船员要知道自己目前所在的位置，船员通过起始点进行推算，使用罗盘等工具记录运动的方向和运动的速度，同时也通过标志建筑的纠正，来确定自己的当前位置。这种方法被推广使用在了室内定位领域中，有着很好的效果。这种方法被推广使用在了室内定位领域中，有着很好的效果。

![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200520232329.png)

### 四、总体设计方案

​       根据系统需求分析，我们可以将本系统分为四个功能模块，它们分别为数据采集模块、定位模块、轨迹跟踪、查找最短路径模块，相应的层次方框图如图所示：

![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200520232359.png)

### 五、软件使用说明

​       基于Android的室内定位系统是基于移动端的应用，下面将按照功能模块的划分对使用流程进行说明，具体分为一下模块：数据采集模块、定位模块、轨迹跟踪、查找最短路径模块。

（1）数据采集模块

​       在使用本模块时首先进入主页面，之后点击信息采集按钮，在信息采集页面填写采集当前采集信号的位置信息，最后点击采集按钮完成WiFi信息采集。在该界面中我们将看到每个参考AP点的信号强度，方便用户感知WiFi信号强度的变化。  

<img src="https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200520232439.png" style="zoom:80%;" />  <img src="https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200520232458.png" style="zoom:80%;" />

（2）定位模块

​       在使用本模块时首先进入主页面，点击定位按钮，在定位页面中，我们将看到自定义地图，之后点击定位按钮，当前的位置信息将显示在界面上。

<img src="https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002120.png" style="zoom:80%;" />  <img src="https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002133.png" style="zoom:80%;" />



（3）轨迹跟踪

​       本模块和定位模块一起集成在定位页面中。

（4）查找最短路径模块

​       在使用模块中首先进入主页面，点击路径规划按钮，在路径规划页面（图5.4）中，我们首先点击定位按钮，获得当前位置，之后输入想要到达的位置，点击导航按钮，完成查找路径功能。

### 六、功能测试

​       本系统测试和使用时不需要知道每个AP点摆放的位置，对室内环境也没有特别要求。在数据采集模块进行前我们首先对室内地图进行绘制如图所示，之后在每个点进行WiFi信号强的的采集，将采集的结果存入数据库中，其结果如图所示

![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002314.png)  ![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002325.png)



​       在定位模块中用户点击定位按钮之后，系统将采集当前位置的WiFi信号强度，将信号强度信息传送至服务器，服务器使用定位算法得到位置，将位置信息传送至Android客户端，并在自定义地图上进行显示，其测试结果如图所示。

​       在轨迹跟踪模块中，系统首先完成定位功能，之后将调用Android的方向传感器和加速度传感器，获得运动步数以及运动方向，通过轨迹跟踪算法获得轨迹信息，其测试结果如图所示，图中蓝点的位置为用户走过的位置，通过这样的方式我们可以获得实时的动态位置和运动轨迹。

<img src="https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002450.png" style="zoom:80%;"/>  ![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002515.png)

​       在查找最短路径模块中，系统首先完成定位功能，之后用户在界面上输入想要到达的位置信息，系统将位置信息传送至服务器，服务器通过路径规划算法，获得路径信息，并将路径信息传送至Android客户端，客户端将其绘制在爱定义地图上，其测试结果如图所示。

<img src="https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002718.png" style="zoom:80%;" />  ![](https://cdn.jsdelivr.net/gh/GXW19961104/photoCloud/blogImg/20200521002737.png)






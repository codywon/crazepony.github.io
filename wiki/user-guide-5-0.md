---
layout: wiki
title: 入手试飞教程
---

> 本教程适合Crazepony-II 5.0版本

## 整机物料列表

* Crazepony四轴飞行器，电机已经安装（1个）
* 正反桨叶（各2只）
* Crazepony遥控器，摇杆已经安装（1个）
* 摇杆帽（2个）
* 遥控器用2.4G无线模块（1个）
* Micro USB数据线（1根）

## 桨叶安装
四轴飞行器的桨叶分为两种，正桨和反桨。安装的时候不能够搞混淆。桨叶上标示有R的安装到M2，M4两个机臂的电机上。标示有L桨叶安装到M1，M3两个机臂电机上。

![](/assets/img/user-guide-5-0-1.jpg)
![](/assets/img/user-guide-5-0-2.jpg)

## 遥控器安装
你拿到Crazepony的包裹的时候，需要自行安装遥控器摇杆帽，没有左右之分。

将2.4G模块安装到遥控器上的排针插座上。模块方向向外。

## 对频解锁试飞
将飞机平放到地面上，电源开关拨到ON，白色电源LED亮起，4个蓝色LED开始闪烁。**飞机进入接收遥控器信号状态。**

打开遥控电源，左上角的白色power灯亮起，左上角信号灯开始间断闪烁，右上角一排蓝色LED常亮后，代表遥控正在工作。

如果对频成功，飞机的四个LED依次旋转两周，最后会变暗，**进入等待解锁状态**。

将左手油门摇杆拉到最低位置，右手方向摇杆打到最左位置然后松手复位，此为解锁手势。

解锁成功后，只有M1和M2臂上的LED开始间断闪烁，crazepony默认是“X”型模式，所以，闪灯的两个臂作为机尾，**应该正对遥控者**。如果未接电池，直接使用usb给飞控电路板供电，则会出现四个LED齐闪烁的现象。

![](/assets/img/user-guide-2.png)

将左手油门摇杆左右反复拨到底几次，让飞控学习到航向角摇杆的操作。**否则会出现航向角无法锁死的问题，即飞起之后四轴飞行器绕中心旋转，即航向角漂移。**

这时候慢慢往上推左手油门遥杆，电机将会开始转动。初次试飞，**一定要到宽阔的户外草地感受摇杆的力度和飞机的灵敏性**。不要到室内测试。或者选择用手拿住飞机，拨动摇杆，感受摇杆各个控制量对飞机姿态的影响

## 遥控器的微调
对于无法垂直起飞的问题，遥控器已经实现了微调功能。定义为遥控器上Key2用于切换是调节横滚（roll）还是俯仰（pitch），Key3表示偏移值增加，Key4表示偏移值减小。这些调节的偏移值会默认被写入STM32的Flash中保存，下次开机之后自动读取。

**飞机起飞向左右偏，需要调节横滚：**

按Key2按键，当LED2亮起的时候，表示可以调节横滚。Key2表示增加，相当于方向摇杆向左打，适合飞机向右偏的情况；Key3表示减小，相当于方向摇杆向右打，适合于飞机向左偏的情况。

**飞机起飞向前后偏，需要调节俯仰：**

按Key2按键，当LED2灭掉的时候，表示进入调节俯仰。Key2表示增加，相当于方向摇杆向前打，适合飞机向后偏的情况；Key3表示减小，相当于方向摇杆向后打，适合于飞机向前偏的情况。

该功能代码已经上传github，还有些不够完善的地方，欢迎测试。

## 电量检测和充电
飞机的四个机臂LED同时出现快速闪烁，则表示飞机电池需要充电。将飞机开关拨到Charge位置，连上usb线则可以充电。可以使用电脑，充电宝，手机充电器等为飞机进行充电。

充电时红色LED亮起，灭掉的时候则表示充电完成。

## 常见问题

##Crazepony的遥控是属于美国手还是日本手？
 
答：美国手。也就是说左手摇杆负责油门和偏航，右手摇杆负责俯仰和横滚。左手摇杆上下为油门控制，左右是偏航控制；右手摇杆上下为俯仰控制，左右为横滚控制

> 有必要科普下什么是日本手：左手摇杆负责俯仰和偏航，右手摇杆负责油门和横滚。是不是很别扭？将俯仰和横滚的控制分离开这种设计太反人类了个人觉得，但是它就是这样一个标准没办法，日本人通常都会做些我们难以理解的事大家都知道的。
 

## 为什么Crazepony的电机臀部老是被戳穿？（有人会在这个时候开始一个劲儿乱喷骂娘，我也很无奈）

答：这么说吧，正常情况下100次起落，都不会对飞机造成任何物理结构上不可逆的毁坏。那么，电机臀部被戳穿这种事情，属于飞机脸先着地的意外，他的臀部是被那根轴顶穿的，空心杯电机其实很脆弱，这个我没办法控制，我已经尽力了。我看了国内的那些用空心杯电机的小四轴，好像都有这个问题...所以，大家提高飞行技术，是对Crazepony最直接的保护。当然，电机坏了，这种事情太好处理了，多准备些空心杯电机，只要主板没坏，随便怎么折腾都可以...


## 无法垂直起飞的问题
答：小伙伴在拿到四轴飞行器试飞的时候，遇到无法垂直起飞的问题，可以从下面4个方面循序渐进，依次改进。

* 电机是否装正了，是否有偏的问题，或者电机轴位置被缠住了（一般是头发，我们就遇到）。
* 整个四轴的重心问题，主要是由于电池位置。你可以根据情况稍稍移动电池位置，改变其重心。
* 通过上面办法要做到完全的垂直起飞还是比较难。但是你可以再起飞的时候稍稍带一点方向遥杆，体验飞行应该是没有问题。我们基本上是做到这一步。
* 进一步的调试方法，那就是遥杆的归中值。也就是说，微调遥杆中间值。有一个上海的伙伴已经这样做了，并且和我们进行了沟通，他在飞控固件中对遥感数据的接收，加入了一个校正偏移量。另外一个方法就是到遥控器上修改，其实很多玩具四轴就是这样做的。就是在遥控器上有4个小按键，用于微调遥感归中值。在我们crazepony遥控器的左下角有几个按键没有焊接，那就可以预留这个作用的。

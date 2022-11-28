# Multi-robot Cooperative Pursuit via Potential Field-Enhanced Reinforcement Learning

人工势场法+多机围捕+强化学习

多机协同使用分散式

贡献：（1）提出了一种新的分散追踪算法，可以有效地学习协同追踪策略，同时利用深度RL和APF的优点。

​            （2） 针对局部极小问题，设计了改进的随墙规则和虚拟障碍物机制。

​            （3）将学习策略应用到现实机器人中

目的：协调集体机器人进行围捕	

解决方法： 设计了强化学习结合人工势场法的混合追踪算法，将人工势场法作为预定义规则融入到学习过程中。(D3QN网络+APF)



对追捕者的行为做出奖励与惩罚

将队友和躲避者视为环境一部分

![img](https://pic2.zhimg.com/v2-73b60f3a13ba0f23ba426b7b2f71acc1_b.png)

R = R_main + R_time + R_tm + R_o + R_pot

抓捕到躲避者时R_main为20否则为0

R_time：用于鼓励追踪者顺利移动

R_tm：是否与队友碰撞

R_o：根据与障碍物之间距离来进行惩罚或奖励





假设实验环境：逃跑者与追赶者之间距离小于设定时被抓住，直至被所有追赶者捕获，任务结束。

![](https://github.com/tt1433669278/cdp/blob/main/Multi-robot/image/360%E6%88%AA%E5%9B%BE20221124105153026.jpg)
E：躲避者

P：追赶者

缺点：使用分散式控制，个体性强不易协调。（可以使用分布集中混合） 

​            没有目标信号，追踪者不可能一直观察到躲避者，不能高效搜索。（可以采用射频追踪，它可以透过墙壁来感知被遮挡的物体） 



# Cooperative Multi-Robot Navigation in Dynamic Environment with Deep Reinforcement Learning

深度强化学习+动态环境+协同导航

目的：基于DRL在复杂环境下实现最优路径

贡献：（1）开发了一种人机相互交换信息以选择最佳目标位置的合作框架。

​            （2）开发DRL框架，学习导航策略生成最优路径。

​            （3）建立了一个训练机制，使策略具有广泛性。

挑战：（1）目标分配低效。

​            （2）缺乏合作方案。

​            （3）从仿真到现实的无效转换。

目的：以最短时间在动态环境中导航到目标位置

方法：深度强化学习，对行为进行奖励和惩罚。

![](https://github.com/tt1433669278/cdp/blob/main/Multi-robot/image/360%E6%88%AA%E5%9B%BE20221128194045299.jpg)


## 采用分散深度强化学习的方法的学习适应动态环境的合作追踪策略

强化学习：

<A, S, R, P>
Action space : A 
State space : S
Reward: R : S × A × S → R
Transition : P :S × A → S 

![](https://github.com/tt1433669278/cdp/blob/main/Multi-robot/image/v2-4c11d459d855896ce3c52cc0718a35c4_b.png)
Reward Signal ：agent目标不是当前reward最大而是累计reward最

Value function ： 长期平均回报的好坏

**Policy**: Policy是指Agent则是在状态s时，所要做出action的选择，定义为![\pi ](http://www.zhihu.com/equation?tex=%5Cpi+)，是RL中  最核心的问题了。policy可以视为在Agent感知到环境后s后到动作a的一个mapping。如果策略是随机的，policy是根据每个动作概率![\pi(a|s)](http://www.zhihu.com/equation?tex=%5Cpi%28a%7Cs%29)选择动作；如果策略是确定性的，policy则是直接根据状态s选择出动作![a=\pi (s)](http://www.zhihu.com/equation?tex=a%3D%5Cpi+%28s%29)。


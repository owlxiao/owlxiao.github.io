<!-- slide -->

#  


<!-- slide -->

思索： 怎样才能设计一个炫酷狂拽 ~~屌炸天~~的机器人？

---


<p align="left">问问ChatGPT：</p>


<img src="./pic/ask-chat-gpt.png" width = "50%" height = "50%"  align=center></img>


<!-- slide vertical=true -->

### 不如把问题细化一下：

* 造一个机器人
* 对抗其他机器人


<!-- slide -->
<p align="left">造一个机器人，一个合理的机器人</p>

---

<p align="left">需求->设计->实物</p>

<div align="left">

* 每一步都可能出错

    * 理想：一气呵成！
    * 现实：差不多得了😅

</div>


<!-- slide vertical=true -->
<div align="left">

好机器人不是**头脑风暴**出来的，是**论证**出来的
* 不是想一出是一出
    * 辛辛苦苦的工作被推翻😂

道理都明确， 但是：
* 硬件又不如软件， 开发周期长
* 调试难度剧增
    * 一步步推翻三座大山


</div>

<!-- slide vertical=true -->

<div align="left">


将软工的**敏捷开发**引入到硬件中
* 软件可以，硬件不行吗？
* 快速找到最优解不就行了吗！😄
* 用最小代价换取最高收益
* 当“领路者“，把所有可能的坑都踩了

**工具就是第一生产力**
* 使用工具/搭建基础设施
    * 短期投入，长期回报

去探索技术的无限可能性

</div>


<!-- slide -->

<div align="left">

功能验证
* 验证机器人模型实现预期功能的可行性
---

依托coppeliasim平台进行建模：
* 在这个层次不需要考虑太多，只需要考虑**干什么可以吗?**
* 借助于coppeliasim的python remote API可以做很多事
    * 丰富的库函数
    * 容易hack的动态语言
    * “人生苦短，我用Python”😄


</div>

<!-- slide vertical=true -->
 <div align="left">

性能验证
* 计算机器人的应力、位移、刚度等性能指标 
---

用abaqus进行机器人的动力学仿真
* 机器人能被敌人撞掉吗？
* 球能射多远？
* ...

</div>

<!-- slide vertical=true -->
<div align="left">

行为验证
* assert Failure， Error，Fault

---

对机器人系统的几个抽象层次进行model checking:
* 世界万物都是状态机 
    * 跟黄金模型进行对比
* 防御性编程有时候太蠢了😂
    * 总不可能assert到处飞把！
        * 硬件就不能用咯
* 在单片机上也不能用sanitizer
    * 抽象层次太低了，我们就是造物者
* **Differential Testing**！！！！

</div>

<!-- slide vertical=true -->

<div align="left">

2022年: 香山团队的DiffTest工作被体系结构国际顶会MICRO录用

--- 
<font size=6>
Yinan Xu, et al. Towards Developing High Performance RISC-V Processors Using Agile Methodology
</font>


</div>

<img src="./pic/difftest-micro.png" width = "70%" height = "70%"  align=center></img>

>


<!-- slide  -->
<div align="left">

如何对抗机器人？提前当好间谍

---

* 知己知彼，百战不殆
* 尝试运用人工智能构建起假想敌
    * 学习往届队伍的机器人行为
        * 这样就可以部署到已有的机器人上，进行模拟对抗
* 最简单的demo
    * CoppeliaSim + Gym 去强化学习

</div>

<!-- slide -->

<div align="left">

不画大饼 - 翻越三座大山的可行性

---

CoppeliaSim和abaqus进行建模仿真

* 易点
    * 停留在用的层次，快速上手 :o:

* 难点
    * 如何联系起整个平台，做全平台仿真 :question:
    * 各个物理层面的仿真：碰撞，应力... :question:
    * 高性能计算 :question:

</div>



<!-- slide vertical=true -->

<div align="left">

Differential Testing

---

* 易点
    * 简单的model checker 很好写 :o:
        * 管他的什么层次trace，观察整个状态空间
        * all in，~~小孩子才做选择~~😄

* 难点
    * 观测不同层次的状态机模型 :question:
        * 现在是整个系统， 复杂程度max！！！


</div>

<!-- slide vertical=true -->
<div align="left">

强化学习

---

《极限速通AI指北》
* 可以试试


</div>

<!-- slide -->
问题？

<!-- slide vertical=true -->

<div align="left">

这有什么用呢？一两个月机器人就搭起来了...

---

* 当然！基础设施的建立都是需要高投入的，正所谓“罪在当代，功在千秋”
* 试想一下后几届的比赛，我们可以直接用自动化继集成工具去验证模型
    * 一键启动
    * ~~不觉得很酷吗 作为一个工科男 我觉得这太酷了 很符合我对未来生活的想象 科技并带着些趣味~~


</div>


<!-- slide vertical=true -->
<div align="left">

香山的基础设施

---

<font size=6>

2021年RISC-V中国峰会, 工具类报告占香山团队报告总量55%

* 大厂里面的基础设施更丰富

</font>

<img src="./pic/xiangshan-tools.png" width = "70%" height = "70%"  align=center></img>

</div>

<!-- slide vertical=true -->
<div align="left">

我不能实际测试吗，非要用仿真

---

没错，诸多东西都可以用经验主义实际去测出来
* ~~我的想法没用~~

随着机器人的复杂度增加，弊端就会暴露出来
* 仿真的意义是提供一个一致性较好、不确定因素可控的评估对象/环境
* 6台车，总不能造出来了再测吧😂
* 车能gank其他的车吗？

</div>


<!-- slide vertical=true -->
<div align="left">

为什么要用coppeliasim和abaqus建模

---

coppeliasim(前V-rep)

* 可以导入solidworks模型
    * [Can we import our Solidworks robot designs into V-REP?](https://forum.coppeliarobotics.com/viewtopic.php?t=17&sid=bc05d8b0e1e5f352ac34aaa82ba7af28)
* 支持C/C++，Python，JAVA，Lua，Matlab编写脚本
    * [Remote API](https://www.coppeliarobotics.com/helpFiles/en/remoteApiOverview.htm)
* 内嵌多种物理引擎
    * [Dynamics](https://www.coppeliarobotics.com/helpFiles/en/dynamicsModule.htm)

</div>

<!-- slide vertical=true -->
<div align="left">

ABAQUS

---

* 支持Solidworks模型导入
* 有强大的材料库
* B站大学有学习资料😂
* 输出的inp文件可以用其他有限元求解器处理
    * 用taichi写的[FEMcy](https://github.com/mo-hanxuan/FEMcy)

</dif>
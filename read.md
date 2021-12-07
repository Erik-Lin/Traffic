# Traffic-query-system

数据结构的设计：
class TrafficSystem:  一个图结构
    struct Vertex:    图中点结构
        int num      唯一标识一个点
        int Distance 点的距离？
        int nowtime  点的时间？
    struct Edge:
        string Start    起点名字
            End      终点名字
            Number   航班号/铁路班次
        int startpoint      起点id
            endpoint        终点id
            begintime       ？
            endtime         ？
            Distance        ？
            cost            票价

用int Total 来唯一表示一个城市，即站点的id
用string City[] 来存储城市名称和站点id，即name与id 一一对应
用map<string,int> Network 来存储所有城市名称和id
用vector<Edge> Plane[] 和 Train[] 来存储所有飞机航线/火车路线

Final design of Data Structure course

计算机科学与技术 19307130266 林山力 

## 一、选题：交通查询系统 

​		【问题描述】 为满足广大复旦教师和学生的出行需要，复旦大学计算机学院邀请你为其开发一款交通 查询 APP。出于不同的目的，教师和学生对交通工具有着不同的要求。 例如，因公出差的 教师希望在旅途中耗费的时间尽可能短，出门旅游的学生则希 望旅费尽可能省，而行动不 便的人则要求中转次数最少。所以，你开发的 APP 需要具备在各个城市间进行线路规划的 能力，能够实时为教师和学生提供两种或三种最优决策的交通咨询。 

​		程序规定有如下设置： 

(1)为评估 APP 是否已经达到预定设计目标，请给出 APP 的运行实例。如对于路线咨询 功能，需要展示：由用户输入起始站、终点站、最优决策原则和交通工具，程序输出最快需 要多长时间才能到达或者最少需要多少旅费才能到达，并详细说明依次于何时乘坐哪一趟列 车或哪一次班机到何地，整个运行流程需在报告中附上截图；

(2) 要求程序有一定鲁棒性，能应对一些错误的输入； 

(3) 不允许使用数据库系统来存储各类信息，只能使用普通文件；

(4) 只需要实现核心数据结构和算法，能从控制台进行输入即可，不需要提供图形化界 面。 

## 二、需求分析-叙述每个模块的功能要求 

1.实现对城市信息进行编辑（如添加或删除）的功能。 

2.假定城市之间有两种交通工具：火车和飞机。实现对列车线路以及飞机航班 班次信 息进行编辑（增设或删除）的功能。班次信息最少应包括：起始站、终点站、出发时间、到 达时间、票价。 

3.打印时刻表。输入城市名称，打印由该城市出发的所有列车路线以及飞机航班班次 信息。 

4.在确定起始站和终点站以及交通工具（全程不变）的情况下，系统应能提供两种最优 决策：最快到达或最省钱到达。（旅途中耗费的总时间应该包括中转等候的时间） 

## 三、概要设计 

- 1.将交通系统设计为一个类，需要的东西全放入类定义。

- 2.用文件存放所有需要的数据，即火车时刻表和航班时刻表，以此搭建交通系统图，整 个交通系统图在这些数据的基础上跑起来。 

- 3.再使用两层循环不断调用类定义中的功能函数，实现 app 的启动和结束。

### 数据结构

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170222688.png" alt="image-20211207170222688" style="zoom:50%;" />

​	交通系统的类定义需要的数据结构 Vertex 代表图中的顶点。Edge 代表图中的边。加上系统中所需要的数据就构成抽象的交通系统图，再将各个数据结构的抽象类定义具化后得到 以上内容，定义旁都有对应的注解。 

PS: 这个图里的“系统所需数据”少写了一个 Total，代表城市个数。 以下为基于以上关键数据结构的功能函数。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170240312.png" alt="image-20211207170240312" style="zoom:50%;" />

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170249317.png" alt="image-20211207170249317" style="zoom:50%;" />

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170256763.png" alt="image-20211207170256763" style="zoom:50%;" />

### 功能函数

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170309397.png" alt="image-20211207170309397" style="zoom:50%;" />

功能函数对应所有基本要求。 四、详细设计 类定义代码都在 Traffic.h 类定义功能函数 #begin#

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170326203.png" alt="image-20211207170326203" style="zoom:50%;" />

构造函数，初始化 Network 以及 Plane[Maxn],Train[Maxn];

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170340218.png" alt="image-20211207170340218" style="zoom:50%;" />

计算需要耗费的时间。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170350392.png" alt="image-20211207170350392" style="zoom:50%;" />

用来选择方案，用对应方案返回路线权值（时间最短/花费最少）

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170403782.png" alt="image-20211207170403782" style="zoom:50%;" />

递归调用，打印整条路线上的所有信息。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170414061.png" alt="image-20211207170414061" style="zoom:50%;" />

换算时间，然后输出。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170427185.png" alt="image-20211207170427185" style="zoom:50%;" />

从文本文件中读取数据，用以搭建基本系统。文件内的数据是从网上找的。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170440121.png" alt="image-20211207170440121" style="zoom:50%;" />

删除路线，用城市名去 Network 里找到这个城市对应的 int，然后回到 edge[]也就是存 放路线信息的 vector 里删除对应路线。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170459298.png" alt="image-20211207170459298" style="zoom:50%;" />

根据输入获取对应交通工具的最短路径（这里 type 就是对应时间或者钱最少）

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170515738.png" alt="image-20211207170515738" style="zoom:50%;" />

用 Dijkstra 算法求最短路径，借助优先级队列来的最小堆获取最小值。结果存在 Distance 数组中，查不到的退出，查到了根据 type 打印最短路径。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170524509.png" alt="image-20211207170524509" style="zoom:50%;" />

增加一条路线。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170544203.png" alt="image-20211207170544203" style="zoom:50%;" />

删除城市以及相关的路线信息。

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170555674.png" alt="image-20211207170555674" style="zoom:50%;" />

打印火车时间表/航班信息表。 类定义功能函数 #end# 主函数会在附在.cpp 文件里 

程序运行界面#begin#

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170610764.png" alt="image-20211207170610764" style="zoom:50%;" />

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170943694.png" alt="image-20211207170943694" style="zoom:50%;" />

程序运行界面#end#

## 五、调试分析 

包括测试数据、测试输出的结果（输出内容要求附上截图）、时间复杂度分析、对每个 模块设计和调试时所存在问题的思考（有哪些问题？问题如何解决？）、 及算法是否可以改 进等。

### 1.关于最优路线的测试数据以及结果：

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170930019.png" alt="image-20211207170930019" style="zoom:50%;" />

### 2.关于新增路线的测试数据以及结果:

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170904010.png" alt="image-20211207170904010" style="zoom:50%;" />

新增成功 现测试新增的路线是否存在并能否使用

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170806383.png" alt="image-20211207170806383" style="zoom:50%;" />

路线加入成功，并且可以正常使用

### 3.现在删除去纽约的火车路线，检测删除路线是否正常

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170816431.png" alt="image-20211207170816431" style="zoom:50%;" />

发现可以正常删除，但是再次查找该路线时，出现了异常，并异常结束了。 经过寻路发现出现问题的是 shortestpath（）函数，我们之前增加了这条路线，然后有删除 了，对于函数中的 Distance[endpoint] 没有置零而是在置了 inf 一个很大的数，所以在这里 修改异常退出条件就是 Distance[endpoint] >= inf/2 。然后重新运行程序，按之前的操作加 入纽约这个城市，加入火车路线，再删除，再查找，发现正常运行了！

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170841817.png" alt="image-20211207170841817" style="zoom:50%;" />

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170849185.png" alt="image-20211207170849185" style="zoom:50%;" />

### 4.关于输出火车时间表/航班信息表

<img src="C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170717930.png" alt="image-20211207170717930" style="zoom:50%;" />

### 5.关于退出系统：

![image-20211207170704798](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20211207170704798.png)

### 6.关于主要算法的时空复杂度分析 

时间复杂度：使用邻接链表处理数据，使用 Dijkstra 算法，复杂度 O(n 平方)。

n 是 城市数量。 空间复杂度：用邻接链表 vector 存储了每一条边，复杂度 O(m)。m 是边数。 

## 六、课程设计总结 

​	课程设计让我从头到尾再次学习了一遍数据结构，无论是学过的类定义，vector 的用法， 文件输入，优先级队列，还是没学过的 map 容器，以及一直云里雾里的 Dijkstra 算法。其实 也尝试过 floyed，还有 prim 算法，但是 bug 更多，就打消了，怕耽误更多时间。但是对于 这些算法的思想的理解是更加深入了。 遇到不会的模块，先翻看了清华的教材以及老师课上的 ppt 解决了很多关于图的问题。 解决不了的，书上没有的，就在网上搜索相关资料，STL 库的一些用法。 关于程序调试，最大的感悟就是，在写程序的时候就尽力将思绪理清楚理透彻，花时间 写出逻辑严密的代码，比草草写完后花更多的时间调 bug 更值得。 关于数据结构课程的认识，从理论向实践迈进。我觉得对于理论的了解更加深入了，并 且我可以使用我学习到的理论知识去解决实际问题，这是让我有最大成就感的地方。 做这个课程设计是从十二月中旬靠后开始的，每天去完成一部分，前七天大概构建了框 架和类定义，接下来每天写一两个功能函数，期间学习了网上他人关于从文件中读入数据的 格式以及文件内容，这个是让我大大加速的地方，文件内容也会附录。最后用了三天左右的 时间优化代码以及完成菜单界面的构建。在这里我也感谢我的舍友帮我纠出程序中的一些优 化问题和 bug，以及边界不完善的漏洞。 

## 七、参考资料 

### 参考书籍： 

1.《数据结构（用面向对象方法与 C++语言描述）》第二版 殷人昆 

2.《Database System Concepts》Sixth Edition 

### 参考网站： 

1. https://www.runoob.com/w3cnote/cpp-vector-container-analysis.html 
2.  http://c.biancheng.net/view/215.html 

3. https://blog.csdn.net/xulingxin/article/details/81335030 
4. https://www.runoob.com/cplusplus/cpp-classes-objects.html 
5. https://blog.csdn.net/wkq0825/article/details/82255984 
6. https://www.w3cschool.cn/cpp/cpp-fu8l2ppt.html 
7. https://www.cnblogs.com/fnlingnzb-learner/p/5833051.html 
8. https://blog.csdn.net/sevenjoin/article/details/81943864 
9. https://blog.csdn.net/Rice__/article/details/106598336  
10. https://blog.csdn.net/qq_39630587/article/details/83240036 
11. http://c.biancheng.net/view/7591.html 
12. https://www.runoob.com/cplusplus/cpp-files-streams.html 
13. https://blog.csdn.net/zhangzhikang_zzk/article/details/50405035?utm_medium=distribue.pc_relevant.none-task-blog-OPENSEARCH-9.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-OPENSEARCH-9.control 
14. https://blog.csdn.net/geter_CS/article/details/102580332 
15. https://blog.csdn.net/nisxiya/article/details/45725857

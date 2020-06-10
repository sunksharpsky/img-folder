# 洛书Lite云脑培训
i
> 培训时间：
>
> 培训人员:
>
> 参加人员：



## １．需求

(https://redmine.uisee.ai/projects/501/)


| 项目                        | 统计                                                         |
| ----------------------------| ------------------------------------------------------------ |
| 动物                        | 里程统计|
|                             | Trip统计|
|                             | P0/P1统计|
|                             | Alert统计|
|                             | 统计图|
| 明珠                        |                                                              |
|                             | Trip统计|
|                             | Alert统计|
|                             | 统计图|

## ２．统计信息

- 统计信息在第二天生成报告

### 2.1 动物-里程统计

**里程数据统计包含的信息：**

![Image text](https://github.com/sunksharpsky/img-folder/blob/master/%E9%87%8C%E7%A8%8B%E7%BB%9F%E8%AE%A1.png)

  1）当天，本周(第一天为星期天)，本月(第一天为当月一号)的自动驾驶里程(单位：KM)。

  2) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的自动驾驶时间(单位：h)。

  3) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的自动驾驶平均速度(单位：KM/h)

- 自动驾驶平均速度=自动驾驶里程÷自动驾驶时间

  4) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的运行时长(单位：h)

  5) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的断开连接次数

- 断开连接：包括人工介入，云端急停，故障急停。

### 2.2 动物-Trips统计

**Trips数据统计包含的信息：**

![Trip数据统计](/home/sk/TestCases/Loshu-lite_TestCases/Trip数据统计.png)

  1）当天Trip数量，卸货Trip数，无卸货Trip数。

- Trip定义：在动物⻋辆中,⻋辆从吊装区站点出发,驾驶一段时间后又回到了吊装区站点为一个完整的流程,我们
将这个完整的流程定义为一个Trip

- 卸货Trip判定：在动物⻋辆中,⻋辆从吊装区站点出发，在卸货区任务状态为进站→到站→任务暂停→进行中（mission_state从4->5,然后从0->3），回到吊装区站点。

**Trips详细统计包含的信息：**

![Trips详细统计](/home/sk/TestCases/Loshu-lite_TestCases/Trips详细统计.png)

  1）统计trip的开始时间、结束时间和时间间隔。

  2）统计trip的开始电量、结束电量、电量差。

  3）统计每个trip的刹车次数、刹车时间(目前es中不包含此数据，无法统计)。

  4）统计每个trip的卸货开始时间、卸货结束时间、卸货时长、卸货点。

**P0/P1错误统计包含的信息：**

![P1错误统计](/home/sk/TestCases/Loshu-lite_TestCases/P1错误统计.png)

  1）P0所在trip，经纬度，开始时间信息。

- P0：出现故障后，自行恢复，计算时间差 （如2min内）

  2）P1所在trip，经纬度，开始时间信息。

- P1：出现故障后，自行恢复或人工恢复（超过2min，或人提前进行了干预，都算P1）

### 2.3 动物-Alert统计

**Alert总结统计包含的信息：**

![Alert总结统计](/home/sk/TestCases/Loshu-lite_TestCases/Alert总结统计.png)

  1）车辆从2019年12月30日以来跑过的总的trip数量，alert事件发生总数、平均每天次数、平均每个trip次数。

**Alert天统计包含的信息：**

![Alert天统计](/home/sk/TestCases/Loshu-lite_TestCases/Alert天统计.png)

  1）车辆当天总的trip数量，alert事件发生总数、平均每天次数、平均每个trip次数。

**Alert细节统计包含的信息：**

![Alert细节统计](/home/sk/TestCases/Loshu-lite_TestCases/Alert细节统计.png)

  1）车辆当天alert事件发生开始时间、结束时间、时间间隔、模块。

**E4/E5 alert stats统计包含的信息：**

![E4E5统计](/home/sk/TestCases/Loshu-lite_TestCases/E4E5统计.png)

  1）车辆当天alert事件level为4或5发生时间、级别、名称。

**error code stats统计包含的信息：**

  1）车辆当天DCU errror code发生的时间、错误代码、消息。

### 2.4 动物-统计图

**当天电量统计图：**

![当天电量统计图](/home/sk/TestCases/Loshu-lite_TestCases/当天电量统计图.png)

  1）车辆当天每个trip消耗电量和当天所有trip消耗的平均电量图。

**里程图：**

![里程图](/home/sk/TestCases/Loshu-lite_TestCases/里程图.png)

  1）车辆当天一个trip里程图。

- 红色部分表示手动驾驶，绿色部分表示自动驾驶，unload_point表示卸货点，箭头表示车辆开始的出发点和出发方向.

**速度热力图：**

![速度热力图](/home/sk/TestCases/Loshu-lite_TestCases/速度热力图.png)

  1）车辆当天一个trip速度热力图。

- 白色部分表示手动驾驶速度，其他部分表示自动驾驶是的速度

**ping lost热力图：**

![pinglost](/home/sk/TestCases/Loshu-lite_TestCases/pinglost.png)

- 目前es中没有相关数据，所以作图为黑色

**定位源置信度热力图：**

![定位源置信度](/home/sk/TestCases/Loshu-lite_TestCases/定位源置信度.png)

  1）车辆当天一个trip定位源置信度热力图。

- gps置信度，此外还有vslam、lslam的置信度

**各个定位元与融合定位源之间差值热力图：**

![差值](/home/sk/TestCases/Loshu-lite_TestCases/差值.png)

- 目前es上没有各个定位源的经纬度与theta角数据，结果如上


## ３．培训反馈


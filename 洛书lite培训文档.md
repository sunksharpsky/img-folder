# 洛书Lite云脑培训

> 培训时间：
>
> 培训人员:
>
> 参加人员：



## １．需求

(https://redmine.uisee.ai/projects/501/)


| 项目                        | 统计信息                                                      |
| ----------------------------| ------------------------------------------------------------ |
| 动物                        |                                                              |
|                             | 里程统计|
|                             | Trip统计|
|                             | P0/P1统计|
|                             | Alert统计|
|                             | 统计图|
| 明珠                        |                                                              |
|                             | Trip统计|
|                             | Alert统计|
|                             | 统计图|

## ２．统计信息

- 统计信息在第二天生成报告，目前在minIO中下载报告。
- 提供了下载api给console，console提供下载界面（开发中）


### 2.1 动物Report


**里程数据统计包含的信息：**

![里程统计dw](/home/sk/TestCases/Loshu-lite_TestCases/里程统计dw.png)

  1）当天，本周(第一天为星期天)，本月(第一天为当月一号)的自动驾驶里程(单位：KM)。

  2) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的自动驾驶时间(单位：h)。

  3) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的自动驾驶平均速度(单位：KM/h)

- 自动驾驶平均速度=自动驾驶里程÷自动驾驶时间

  4) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的运行时长(单位：h)

  5) 当天，本周(第一天为星期天)，本月(第一天为当月一号)的断开连接次数

- 断开连接：包括人工介入，云端急停，故障急停。


**Trips数据统计包含的信息：**

![Trip数据统计dw](/home/sk/TestCases/Loshu-lite_TestCases/Trip数据统计dw.png)

  1）当天Trip数量，卸货Trip数，无卸货Trip数。

- Trip定义：在动物⻋辆中,⻋辆从吊装区站点出发,驾驶一段时间后又回到了吊装区站点为一个完整的流程,我们
将这个完整的流程定义为一个Trip

- 卸货Trip判定：在动物⻋辆中,⻋辆从吊装区站点出发，在卸货区任务状态为进站→到站→任务暂停→进行中（mission_state从4->5,然后从0->3），回到吊装区站点。


**Trips详细统计包含的信息：**

![Trips详细统计dw](/home/sk/TestCases/Loshu-lite_TestCases/Trips详细统计dw.png)

  1）统计trip的开始时间、结束时间和时间间隔。

  2）统计trip的开始电量、结束电量、电量差。

  3）统计每个trip的刹车次数、刹车时间(目前es中不包含此数据，无法统计)。

  4）统计每个trip的卸货开始时间、卸货结束时间、卸货时长、卸货点。


**P0/P1错误统计包含的信息：**

![P1错误统计dw](/home/sk/TestCases/Loshu-lite_TestCases/P1错误统计dw.png)

  1）P0所在trip，经纬度，开始时间信息。

- P0：出现故障后，2min内自行恢复。

  2）P1所在trip，经纬度，开始时间信息。

- P1：出现故障后，自行恢复或人工恢复（超过2min，或人提前进行了干预）。


**Alert总结统计包含的信息：**

![Alert总结统计dw](/home/sk/TestCases/Loshu-lite_TestCases/Alert总结统计dw.png)

  1）车辆从2019年12月30日以来跑过的总的trip数量，alert事件发生总数、平均每天次数、平均每个trip次数。


**Alert天统计包含的信息：**

![Alert天统计dw](/home/sk/TestCases/Loshu-lite_TestCases/Alert天统计dw.png)

  1）车辆当天总的trip数量，alert事件发生总数、平均每天次数、平均每个trip次数。


**Alert细节统计包含的信息：**

![Alert细节统计dw](/home/sk/TestCases/Loshu-lite_TestCases/Alert细节统计dw.png)

  1）车辆当天alert事件发生开始时间、结束时间、时间间隔、模块。


**E4/E5 alert stats统计包含的信息：**

![E4E5统计dw](/home/sk/TestCases/Loshu-lite_TestCases/E4E5统计dw.png)

  1）车辆当天alert事件level为4或5发生时间、级别、名称。


**error code stats统计包含的信息：**

![errorcodestats统计dw](/home/sk/TestCases/Loshu-lite_TestCases/errorcodestats统计dw.png)

  1）车辆当天DCU error code发生的时间、错误代码、消息。


**当天电量统计图：**

![当天电量统计图dw](/home/sk/TestCases/Loshu-lite_TestCases/当天电量统计图dw.png)

  1）车辆当天每个trip消耗电量和当天所有trip消耗的平均电量图。


**里程图：**

![里程图dw](/home/sk/TestCases/Loshu-lite_TestCases/里程图dw.png)

  1）车辆当天一个trip里程图。

- 红色部分表示手动驾驶，绿色部分表示自动驾驶，unload_point表示卸货点，箭头表示车辆开始的出发点和出发方向。


**速度热力图：**

![速度热力图dw](/home/sk/TestCases/Loshu-lite_TestCases/速度热力图dw.png)

  1）车辆当天一个trip速度热力图。

- 白色部分表示手动驾驶，其他部分表示自动驾驶时的速度。


**ping lost热力图：**

![pinglostdw](/home/sk/TestCases/Loshu-lite_TestCases/pinglostdw.png)

- 目前es中没有相关数据，所以作图为黑色


**定位源置信度热力图：**

![定位源置信度dw](/home/sk/TestCases/Loshu-lite_TestCases/定位源置信度dw.png)

  1）车辆当天一个trip定位源置信度热力图。

- gps置信度，此外还有vslam、lslam的置信度


**各个定位元与融合定位源之间差值热力图：**

![差值dw](/home/sk/TestCases/Loshu-lite_TestCases/差值dw.png)

- 目前es上没有各个定位源的经纬度与theta角数据，结果如上


### 2.2 明珠Report


**Trips数据统计包含的信息：**

![Trips数据统计mz](/home/sk/TestCases/Loshu-lite_TestCases/Trips数据统计mz.png)

  1）HTML格式：统计当天trip的总数、自动驾驶Trip数量、达标数量(10分钟以内)、Trip合格率、超时数量(10分钟以上)、Trip超时率。

- trip定义：从A1出发到达行李大堂或从行李大堂出发到达A1，定义为一次trip。

- 达标数量(10分钟以内)/超时数量(10分钟以上)：一次trip在10分钟内完成为达标，否则为超时。

- Trip合格率=达标数量 ÷ 自动驾驶Trip数量

- Trip超时率=超时数量 ÷ 自动驾驶Trip数量

  2）EXCEL格式，sheet:Trip_custom、Trip

- Trip_custom：给用户看（路线：A to C/C to A）；Trip：给研发看（路线：A to B/C to A）。

- 当天每个trip开始时间，结束时间，时间间隔。

- 当天每个trip开始电量，结束电量，消耗电量。

- 当天每个trip车辆暂停原因，有四种分别是RMU_Pause, layby（进入避障处）,stop by obstacle（障碍物停车），take_over_state变为变为值1或者4（表示车辆进入人工状态或者人工介入状态）。

- 速度统计

  3）EXCEL格式，sheet:vehicle_static

- 当天车辆暂停的trip编号，路线（STA/ATS），暂停开始时间，暂停持续时间，位置，路段（Section1/2/3/4）,暂停原因，暂停命令发出时间，发出到成功执行时间间隔。

  4）EXCEL格式，sheet:Daily

- 当月每天自动驾驶Trip数量、达标数量(10分钟以内)、Trip合格率、超时数量(10分钟以上)、Trip超时率。

  5）EXCEL格式，sheet:Weekly

- 当月每周自动驾驶Trip数量、达标数量(10分钟以内)、Trip合格率、超时数量(10分钟以上)、Trip超时率。

  6）EXCEL格式，sheet:Monthly

- 当月自动驾驶Trip统计。


**Alert总结统计包含的信息：**

![Alert总结统计mz](/home/sk/TestCases/Loshu-lite_TestCases/Alert总结统计mz.png)

  1）HTML格式，EXCEL格式（sheet：alert_summary）：车辆从2019年12月30日以来跑过的总的trip数量，alert事件发生总数、平均每天次数、平均每个trip次数。


**Alert天统计包含的信息：**

![Alert天统计mz](/home/sk/TestCases/Loshu-lite_TestCases/Alert天统计mz.png)

  1）HTML格式，EXCEL格式（sheet：alert_day）：车辆当天总的trip数量，alert事件发生总数、平均每天次数、平均每个trip次数。


**Alert细节统计包含的信息：**

![Alert细节统计mz](/home/sk/TestCases/Loshu-lite_TestCases/Alert细节统计mz.png)

  1）HTML格式，EXCEL格式（sheet：alert_detail）：车辆当天alert事件发生开始时间、结束时间、时间间隔、模块。


**E4/E5 alert stats统计包含的信息：**

![E4E5统计mz](/home/sk/TestCases/Loshu-lite_TestCases/E4E5统计mz.png)

  1）车辆当天alert事件level为4或5发生时间、级别、名称。


**error code stats统计包含的信息：**

![errorcodestats统计mz](/home/sk/TestCases/Loshu-lite_TestCases/errorcodestats统计mz.png)

  1）车辆当天DCU error code发生的时间、错误代码、消息。


**Week Status统计图：**

![WeekStatusmz](/home/sk/TestCases/Loshu-lite_TestCases/WeekStatusmz.png)

  1）车辆一周内每天自动驾驶trip总数，合格trip数，合格率。


**Day Status统计图：**

![DayStatusmz](/home/sk/TestCases/Loshu-lite_TestCases/DayStatusmz.png)

  1）当天车辆每个trip耗时，耗电量。


**里程图：**

![里程图mz](/home/sk/TestCases/Loshu-lite_TestCases/里程图mz.png)

  1）车辆当天一个trip里程图。

- 红色部分表示手动驾驶，绿色部分表示自动驾驶，trip总耗时，每个路段耗时，暂停时间，A站点（到达/出发）。


**速度图：**

![速度图mz](/home/sk/TestCases/Loshu-lite_TestCases/速度图mz.png)

  1）车辆当天一个trip速度图。


**速度热力图：**

![速度热力图mz](/home/sk/TestCases/Loshu-lite_TestCases/速度热力图mz.png)

  1）车辆当天一个trip速度热力图。

- 白色部分表示手动驾驶，其他部分表示自动驾驶时的速度。


**brake level 3d图：**

![brakelevelmz](/home/sk/TestCases/Loshu-lite_TestCases/brakelevelmz.png)

  1）车辆当天一个trip的brake level 3d图。


**ping lost热力图：**

![pinglostmz](/home/sk/TestCases/Loshu-lite_TestCases/pinglostmz.png)

- 目前es中没有相关数据，所以作图为黑色。


**定位源置信度热力图：**

![定位源置信度mz](/home/sk/TestCases/Loshu-lite_TestCases/定位源置信度mz.png)

  1）车辆当天一个trip定位源置信度热力图。

- gps置信度，此外还有vslam、lslam的置信度


**各个定位元与融合定位源之间差值热力图：**

![差值mz](/home/sk/TestCases/Loshu-lite_TestCases/差值mz.png)

- 目前es上没有各个定位源的经纬度与theta角数据，结果如上



## ３．培训反馈


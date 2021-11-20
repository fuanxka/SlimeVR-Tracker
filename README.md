# SlimeVR-Tracker

## 声明
二次开发请注明原作者、出处以及相关开源协议。<br>
源PCB工程文件需使用Kicad5.99进行查看与编辑。<br>
**详细描述请看：https://sukimoe.net/projects/slimevr-tracker.html**



## 描述
目前SlimeVR的DIY方案为ESP8266/ESP32开发板+TP4056充电模块。这个方案存在一点问题，有点不够优雅：
- 开发板一般用的是MicroUSB接口，而充电模块用的是Type-C接口，如果需要更新固件你可能会满地找数据线。
- 两个接口不美观，且充电模块需要占用额外空间，导致DIY的成品会叠罗汉一样叠上三层。
- 锂电池直连3.3V引脚，而锂电池充满电的时电压为4.2V，具有一定风险。
- 没有合适的外壳，直接上身未免太极客了一点。

基于上述原因，诞生了这个项目，解决了上面的问题，并具有以下特点：
- 超小尺寸，超高集成度，仅比开发板长1mm。
- 整合接口，仅用一个Type-C接口实现充电与程序下载。
- 集成最最最重要的电池保护芯片。
- 预留电池引脚接口和开关引脚接口，锂电池不再直连3.3V引脚，而是会先经过降压芯片降压后输出。
- 智能切换供电，在有外部USB供电的情况下会切断锂电池供电并进行充电，断开供电后自动使用锂电池供电。
- 免驱哒！当连接电脑需要下载程序时，无需额外下载驱动，可直接识别通信。



### 规格尺寸
- PCB尺寸：25mm\*49mm\*1.6mm
- 外壳体积：53.2mm\*38mm\*21.6mm
- 传感器：BNO08X
- 电池：122530锂电池
- 开关：SS-12D07G3
- 导线：26AWG/28AWG
- 固定螺丝：6颗M2\*5
- 绑带：宽度3cm



### 电气参数
部分参数仅供参考，以实测为准。
锂电池充电电流不计算在负载内。
- USB供电电压：5V
- 工作电流：100mA
- 最大负载：500mA
- 充电电流：≤500mA
- 电池容量：1000mA
- 工作时间：约7-9小时



## 注意事项
**选型**
- TP4057芯片需选用`南京拓微`的，友台的数据手册部分数据有差异，可能会出现未知问题。
- 固定螺丝需要选用`薄头自攻螺丝`，头部直径≤4mm，头部厚度≤1mm。
- 传感器如BNO系列价格太高可选用MPU9250，但需要核对尺寸。

**焊接**
- 如果只有电烙铁可以不焊接CH9340K的底部EP焊盘，将不支持睡眠低功耗模式，详情请参阅该芯片数据手册。
- 因焊接工作量较大，建议使用锡膏和加热台进行铁板烧。

**烧录**
- 附件提供编译好的固件（编译自[SlimeVR-Tracker-ESP](https://github.com/SlimeVR/SlimeVR-Tracker-ESP)），也可自行下载编译。
- 请使用`ESP8266Flasher`进行程序烧录工作，波特率`115200`，`4Mbyte`，`40MHz`，`DIO`。


**使用**
- 使用时追踪器朝向需匹配固件配置，建议充电口朝下.有螺丝的那面朝自己。
- 如魔术贴比较硬，无弹性，建议无螺丝的一面朝自己，防止崩短穿孔，同时在软件中调整设置。
- 也可以选择不穿魔术贴，取一段单面的毛面魔术贴，粘贴到追踪器有螺丝的一面。



## 下载
(SlimeVR-Tracker)[https://github.com/FuAnMoe/SlimeVR-Tracker/archive/refs/heads/main.zip]

### SlimeVR软件/固件
> SlimeVR固件：[SlimeVR-Tracker-ESP](https://github.com/SlimeVR/SlimeVR-Tracker-ESP)<br>
> SlimeVR服务：[SlimeVR-Server](https://github.com/SlimeVR/SlimeVR-Server)<br>
> SlimeVR驱动：[SlimeVR-OpenVR-Driver](https://github.com/SlimeVR/SlimeVR-OpenVR-Driver)

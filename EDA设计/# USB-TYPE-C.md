# USB-TYPE-C

- USB TypeC 拥有诸多优点：双面可插不担心正反、可做USB/雷电高速传输载体，支持 PD快充、音频设备、HDMI传输、调试模式等诸多功能。

- 市面上的其他USB接口和充电接口在逐步被TypeC替代，可以预见的是，TypeC作为一种多兼容性接口，其未来会具有非常长的生命周期。

- 主要说明24P、16P、6P USB-TypeC接口的引脚定义，和USB-PD、USB接口类型，方便制作硬件设计时的参考。

## 24P TYPE-C

---

### **母头**

---

![24p 母头](https://img-blog.csdnimg.cn/img_convert/3f8e5b5c01fbf93cfdb2deb986b41add.png)

<br><br>

---

### **公头**

---

![24p 公头](https://img-blog.csdnimg.cn/img_convert/74e75282a1f97a554812804d4d3e6adb.png)

<br><br>

> 插口内的Pin功能相对于中心对称。公头插入母头，无论正反插，引脚功能都完美契合。而且电源VBUS/GND都拥有4个Pin，最大支持5A电流，在保证高速数据传输的同时也提高了电流承载能力。

---
---

### **引脚功能分布**

![24p 公头](https://img-blog.csdnimg.cn/img_convert/25b69d5c451bf687cc4cf11382d0a8f3.png)

---
---

Pin | 名称 | 功能描述 | Pin | 名称 | 功能描述
:---: | :---: | :---: | :---: | :---: | :---:
A1 | GND | 接地 | B12 | GND | 接地
A2 | SSTXp1 | SuperSpeed差分信号#1，TX，正 | B11 | SSRXp1 | SuperSpeed差分信号#1，RX，正
A3 | SSTXn1 | SuperSpeed差分信号#1，TX，负 | B10 | SSRXn1 | SuperSpeed差分信号#1，RX，负
A4 | VBUS | 总线电源 | B9 | VBUS | 总线电源
A5 | CC1 | Configuration channel | B8 | SBU2 | Sideband use (SBU)
A6 | Dp1 | USB 2.0差分信号，position 1，正 | B7 | Dn2 | USB 2.0差分信号，position 2，负
A7 | Dn1 | USB 2.0差分信号，position 1，负 | B6 | Dp2 | USB 2.0差分信号，position 2，正
A8 | SBU1 | Sideband use (SBU) | B5 | CC2 | Configuration channel
A9 | VBUS | 总线电源 | B4 | VBUS | 总线电源
A10 | SSRXn2 | SuperSpeed差分信号#2，RX，负 | B3 | SSTXn2 | SuperSpeed差分信号#2，TX，负
A11 | SSRXp2 | SuperSpeed差分信号#2，RX，正 | B2 | SSTXp2 | SuperSpeed差分信号#2，TX，正
A12 | GND | 接地 | B1 | GND | 接地

---
---

> USB 2.0差分信号只会连接其中一边。USB Type-C 插头 无B6、B7。

---
---

<br><br>

## **16P TYPE-C(12P TYPE-C)**

---
---

### **16p_引脚定义**

![16p_引脚定义](https://img-blog.csdnimg.cn/img_convert/76eb93d1b65132fe172c489658e94258.png)

---
---

> 16Pin TypeC在24Pin的基础上阉割了USB3.0的TX1/2、RX1/2，保留了SBU1/2、CC1/2、USB2.0的D+D-，除了没有USB3.0/3.1高速传输外，其他别无二致，同样支持 PD快充、音频设备、HDMI传输、调试模式等功能。
>>16Pin一般为接口厂家、封装的正式名称，平时使用时习惯称呼为12Pin。在接口设计时，将TypeC母座两端的两个Vbus和GND出线都并拢了起来，实际是16条出线，但焊接的焊盘只要12个。

### **16p_封装**

![16p_封装](https://img-blog.csdnimg.cn/img_convert/35d2ab19a5e4f62424cdb6dba48958c1.png)

## **6P TYPE-C**

- 对于玩具、牙刷等生活用品，产品定位上没有USB通信的需求，只需要USB取电充电。那么连USB2.0都可以省掉了。6Pin TypeC正式出道。
- 6Pin TypeC仅仅保留Vbus、GND、CC1、CC2。接口两侧对称分布着两组GND、Vbus，使得防反插功能保留，粗线也让其更为方便的传输大电流。
- CC1、CC2用于PD设备识别，承载USB-PD的通信，以向供电端请求电源供给。在传输电力的同时，USB数据传输不会受到影响。

---
---

### **6p_母头**

![6p_母头](https://img-blog.csdnimg.cn/img_convert/01bb276a77567a45a334ed3341a0cbbe.png)

### **6p_封装**

![6p_封装](https://img-blog.csdnimg.cn/img_convert/52e43f959005e6dc06a33d76186ecf57.png)

---
---

## CC1、CC2的作用 - 设备识别、PD快充

> 高通CPU的QC快充通过提高输电电压，来提高输送功率。但QC协议中，通信使用的是USB的DP、DM，会导致充电的时候会对USB通信造成影响。<br>
> 而USB-PD对电源设备的识别依靠CC1、CC2引脚，避免了QC标准与DP、DM的冲突。使得USB-PD在传输电力的同时，数据传输不会受到影响。

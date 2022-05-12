
# GPM
---

## Introduction 
Global Preciptation Mesurement 是一个国际卫星网络，提供下一代全球雨雪观测，以促进我们对地球水和能量循环的了解，改进对极端事件的预测，并提供准确及时的信息，直接造福社会。  
GPM的数据产品主要分为三: Level-1, Level-2和Level-3。Level-1就是卫星上各观测仪器的基数据。Level-1还分为Level-1A，Level-1B和Level-1C。Level-1A是指探测仪器直接接收的信号，例如雷达接收到的波能量。Level-1B是将Level-1A收集的信号转化成各类探测变量的单位，例如雷达反射率。Level-1C是针对微波仪的亮温观测，去除掉各个传感器以及多卫星降水反演算法之间的系统误差。Level-1中的基数据包含了各个观测仪器的原始分辨率，可以用来进行特定的算法计算以及其他用途。也就是说，只要有方法，想干什么干什么，但是很难。  
Level-2中的数据是以Level-1的基数据为基础，在相同的分辨率和位置上导出的地球物理变量，例如ku波长的雷达反演的降水以及雷达与微波成像仪合成的降水等。Level-2的降水资料可以用来进行个例分析，地面降水验证以及模式验证等。大家可以赶紧开始对比验证啊！仿佛看到文章雨正在倾盆而下。  
Level-3中的数据则是又在Level-2的基础上插值到固定时间、空间分辨率的格点上，比较完整并且具有较高的一致性。主要提供半小时降水、日降水以及月平均降水的格点资料。半小时降水利用多卫星降水反演获得，日降水是综合了微波成像仪以及多频率降水雷达，月平均降水则包含了以上所有。使用最广泛的数据是多卫星、多传感器以及多算法的GPM综合反演产品(IMERG)，包括**Early**，**Late**和**Final Run**产品。这三者的区别在于发布时间。**Early Run**表示获得观测数据后6h发布，**Late**和**Final Run**分别在18小时以及4个月后发布。Early和Late Run的IMERG产品主要是几乎实时的观测，并且用气候站进行检验校准。Final Run则是利用全球降水气候中心的月平均站点资料进行误差订正。他们的空间分辨率是0.1°，时间分辨率是半小时，都比TRMM降水观测有大大的提高。高时空分辨率的降水观测资料对于降水时间以及业务预报都具有相当重大的意义。月平均资料则可以用来加深对全球降水观测不确定性的理解。[来源](https://mp.weixin.qq.com/s/5EF1RJRsTXzJP36MLE6Mtw)  
项目主要用的是Later Run的日累计降水，格式为Geotiff，方便处理  
* 主站[GPM](https://gpm.nasa.gov/data/directory)

## 主要信息  
||IMERG Early run|IMERG Late run|IMERG Final run|
|---|---|---|---|
|Version|V06B|V06B|V06B|
|Dates Covered|June 2000 - Present|June 2000 - Present|June 2000 - Present|
|Minimum Latency|4 hours|12 Hours|3.5 Months|
|Spation Resoluton|10km / 0.1 Degree|10km / 0.1 Degree|10km / 0.1 Degree|

eg. 
3B-HHR-L.MS.MRG.3IMERG.20220101-S143000-E145959.0870.V06B.1day.tif    
3B:   
L: IMERG Late Run  
HHR: Hour (Maybe)  
MS:  
MRG:  
3IMERG:  
20220101-S143000-E145959:数据获取时间，S143000 为Start 14:30:00, E145959为 End 14:59:59  
0870:  
V06B:数据版本  
1day: 数据时间  

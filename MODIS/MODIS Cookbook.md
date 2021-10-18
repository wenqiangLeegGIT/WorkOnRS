
# **MODIS Series** 
---

## **介绍**
MODIS(中分辨率成像光谱辐射计)指搭载在Terra和Aqua卫星上的载荷。Terra卫星于1999年12月18日发射，Aqua卫星于2002年5月4日发射。它的观测带宽度为2330公里，每**一到两天**观测一次地球的整个表面。
它的探测器测量**36**个光谱波段，并以三种空间分辨率采集数据：250米、500米和1000米。  
## **命名规则**
MODIS产品命名规则根据不同的产品表现形式分为三种，分别为：swath、tile、Climate Modeling Grid (CMG)。 注意，在每种产品命名开始都会有product short name，其中又会包含三种模式，MOD指搭载在Terra星上的MODIS载荷，MYD指搭载在Aqua星上的MODIS载荷，MCD则指产品是由MOD和MYD产品合成而来。 
- swath  
eg: MOD14.A2019159.2345.006.2019160032437.hdf  
此例中，MOD14为产品短名，A（Acquisition） 指获得时间，此例中获得时间为2019159，159指2019年的第159天，2345指更加具体的获取时间，即2019年第159天的23:45，此后的2019160032437指产品生成时间。  
- tile  
eg. MOD09A1.A2006001.h08v05.006.2015113045801.hdf 
此例中，MOD09A1为产品短名，A及后续时间与swath相同，h08v05指tile的条带号，006指Collection的版本，2015113045801指产品生成时间。  
- CMG  
eg. MOD09CMG.A2019169.006.2019171025907.hdf
此例参考swath和tile命名规则。  

## 时空分辨率
- 时间分辨率  
Daily, 4-Day, 8-Day, 16-Day, Monthly, Quarterly, Yearly  
- 空间分辨率  
Bands 1–2 – 250 meter  
Bands 3–7 – 500 meter  
Bands 8–36 – 1000 meter  

## 条带系统
- Sinusoidal Tile Grid（正弦栅格投影）  
大部分标准的MODIS陆地产品使用的是正弦投影系统。在赤道出，tile大小为10°*10°，整个条带系统左上角坐标从(0,0)开始，方向为（水平，垂直），右下角为(h35,v17)。  
- 条带文件  
[中国区域MODIS条带号](http://bbs.sciencenet.cn/home.php?mod=attachment&filename=modis%D0%D0%C1%D0%BA%C5.jpg&id=261592) 

## MODIS数据处理等级
|等级|描述|
|:---|:---|
|Level 0|以全分辨率重建、未处理的仪器和有效载荷数据，并移除任何和所有通信伪影（例如，同步帧、通信头、重复数据）(在大多数情况下，EOS数据和操作系统（EDOS）将这些数据作为生产数据集提供给数据中心，供科学数据处理部门（SDPS）或SIPS处理，以生产更高级别的产品。）|
|Level 1A|以全分辨率、时间参考和附加辅助信息（包括辐射和几何定标系数以及地理参考参数（例如，平台星历）的方式重建、未处理的仪器数据，但不应用于0级数据。|
|Level 1B|已处理至传感器单元的1A级数据（并非所有仪器都具有1B级源数据）。|
|Level 2|以与1级源数据相同的分辨率和位置导出地球物理变量。与一级源数据（swath产品）具有相同分辨率和位置的衍生地球物理变量。***NOTE:LP DAAC从此等级开始分发数据***|
|Level 2G|在统一时空网格比例（正弦）上映射的二级数据.|
|Level 3|映射在统一时空网格尺度上的变量，通常具有一定的完整性和一致性。|
|Level 4|模型输出或low-level数据分析的结果（例如，从多个测量中得出的变量）。|


### 数据来源
- USGS EarthExplorer https://earthexplorer.usgs.gov/
- Google Earth Engine https://earthengine.google.com/
- U.S. GOVERNMENT COMPUTER https://e4ftl01.cr.usgs.gov/ ,此方法相当于直连MODIS数据服务器，在明确知道需要数据的条带号等信息条件下下载非常方便，但需要EARTH DATA 账号。此外还包含GEDI/VIIRS等数据。

问题：一直在找关于MODIS数据综合的一个User guide，但是没有找到，MODIS产品众多，每种产品都有相关的technical report所以无法总结为一个文档。
[这里](https://wenku.baidu.com/view/6fd329dcf524ccbff0218440.html#)是网上找到的一个对MODIS常用数据产品的说明。






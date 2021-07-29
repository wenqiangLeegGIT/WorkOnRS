# Landsat Series
---


## Landsat 8

Landsat8于**2013年2月11日**发射升空，携带有两个主要载荷：**OLI和TIRS**。其中**OLI（全称：Operational Land Imager ，陆地成像仪）** 由卡罗拉多州的鲍尔航天技术公司研制；
**TIRS（全称：Thermal Infrared Sensor，热红外传感器）**，由NASA的戈达德太空飞行中心研制。设计使用寿命为至少5年。OLI陆地成像仪包括**9个波段**，空间分辨率为**30米**，其中
包括一个15米的全色波段，成像宽幅为185x185km。OLI包括了ETM+传感器所有的波段，为了避免大气吸收特征，OLI对波段进行了重新调整，比较大的调整是OLI Band5(0.845–0.885 μm)，排除了
0.825μm处水汽吸收特征；OLI全色波段Band8波段范围较窄，这种方式可以在全色图像上更好区分植被和无植被特征；此外还有两个新增的波段：蓝色波段 (band 1 0.433–0.453 μm) 主要应用海
岸带观测，短波红外波段(band 9 1.360–1.390 μm) 包括水汽强吸收特征可用于云检测；近红外band5和短波红外band9与MODIS对应的波段接近。TIRS 包括2个单独的热红外波段，分辨率100米。


### 数据来源
- USGS EarthExplorer https://earthexplorer.usgs.gov/
- Google Earth Engine https://earthengine.google.com/

### 波段信息

|波段|波长范围um|空间分辨率（米）|主要应用|
|---|---|:---:|---|
|Band 1 Coastal(海岸波段)|0.433-0.453|30|主要用于海岸带观测|
|Band 2 Blue(蓝波段)|0.450-0.515|30|用于水体穿透，分辨土壤植被|
|Band 3 Green(绿波段)|0.525-0.600|30|用于分辨植被|
|Band 4 Red(红波段)|0.630-0.680|30|处于叶绿素吸收区，用于观测道路，裸露土壤，植被种类等|
|Band 5 NIR(近红外波段)|0.845–0.885|30|用于估算生物量，分辨潮湿土壤|
|Band 6 SWIR 1(短波红外1)|1.560–1.660|30|用于分辨道路，裸露土壤，水，还能在不同植被之间有好的对比度，并且有较好的大气、云雾分辨能力|
|Band 7 SWIR 2(短波红外2)|2.100–2.300|30|用于岩石，矿物的分辨很有用，也可用于辨识植被覆盖和湿润土壤|
|Band 8 Pan（全色波段）|0.500–0.680|15|为15米分辨率的黑白图像，用于增强分辨率|
|Band 9 Cirrus（卷云波段）|1.360–1.390|30|包含水汽强吸收特征，可用于云检测|
|Band 10 TIRS 1（热红外1）|10.60 -11.190|100|感应热辐射的目标|
|Band 11 TIRS 2（热红外2)|11.50 -12.51|100|感应热辐射的目标|

### 命名规则

`LXSS_LLLL_PPPRRR_YYYYMMDD_yyyymmdd_CC_TX`  
`LC08_L2SP_127031_20150818_20200908_02_T1.tar.gz`  

|名称标识|描述|
|:---:|:---|
|L|Landsat
|X|说明本产品使用何种传感器，如C代表TIRS和OLI
|SS|Landsat系列卫星编号，08代表 landsat 8，09代表 landsat 9
|LLLL|预处理等级，如L2SP(Level 2 Science Product)，L2SR(Level 2 Surface Reflectance)
|PPP|以Worldwide Reference System-2 (WRS-2) 为参考，卫星产品所在path 如128
|RRR|以WRS-2 为参考，卫星产品所在row 如030
|YYYY|影像产品**获取**年份
|MM|影像产品获取月份
|DD|影像产品获取天
|yyyy|影像产品**处理**年份
|mm|影像产品处理月份
|dd|影像产品获取天
|CC|影像产品集合标识(Collection number) 如 C2,C1
|TX|影像产品集合质量分类 ，"T1" 代表Tier 1(质量最优)，"T2" 代表Tier 2



更多详细信息参见  [Landsat 8-9 OLI-TIRS Collection 2 Level 2 Data Format Control Book](https://prd-wret.s3.us-west-2.amazonaws.com/assets/palladium/production/atoms/files/LSDS-1328_Landsat8-9-OLI-TIRS-C2-L2-DFCB-v6.pdf)




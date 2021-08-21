
# Sentinel series
---
# **Sentinel 2**  
## 1. Intro
SENTINEL-2于2015年6月23日发射,隶属于欧盟委员会哥白尼计划的一部分。Sentinel2旨在提供丰富的数据和图像。该卫星配备了一个光电多光谱传感器（MSI），用于在可见光、近红外(VNIR)和短波红外(SWIR)
光谱区以10至60米的分辨率进行测量。其中包括**13**个光谱通道，确保捕捉植被状态的差异，包括时间变化，同时也将对大气摄影质量的影响降到最低。轨道的平均高度为**785**公里，任务中两颗卫星的存在使得赤道每
**5天**重复调查一次，中纬度每2-3天重复调查一次。Sentinel-2数据提供了由欧洲委员会(EC)和欧洲航天局(ESA)联合实施的GMES(全球环境与安全监测)计划，该计划涉及土地管理、农业生产和林业、自然灾害监测和
人道主义行动等方面的服务。

## 2. **命名规则**
[Sentinel-2_User_Handbook](https://github.com/wenqiangLeegGIT/WorkOnRS/blob/main/Sentinel/Sentinel-2_User_Handbook.pdf)中描述的命名规则与在USGS查询到的数据命名并不相符，查询其他资料后
[ESA](https://sentinel.esa.int/web/sentinel/user-guides/sentinel-2-msi/naming-convention)上指出命名规则有新旧之分，目前提供的数据都是按照新的命名规则来的。  
以USGS Earth Explorer搜索Sentinel 数据结果为例，其元数据中`Vendor Product ID`符合以下命名规则：  
MMM_MSIXXX_YYYYMMDDHHMMSS_Nxxyy_ROOO_Txxxxx_<Product Discriminator>.SAFE  
eg. S2A_MSIL1C_20170105T013442_N0204_R031_T53NMJ_20170105T013443.SAFE  

|Identifier|Descrpition|example|
|---|---|---|
|MMM|Sentinel 2卫星编号|S2A/S2B|
|MSIXXX|产品等级|MSIL1C/MSIL2A|
|YYYYMMDDHHMMSS|数据获取事件|20170105T013442|
|Nxxyy|PDGS处理基线编码|N0204|
|ROOO|相对轨道编码(R001 - R143)|R031|
|Txxxxx|Tile编码|T53NMJ|
|Product Discriminator|-|20170105T013443|
|SAFE|产品格式 (Standard Archive Format for Europe)|-|
  
## 3. **波段信息**  
|Sensor|Band number|Band name|s2a central wavelength(nm)|s2a band width(nm)|s2b central wavelength(nm)|s2b band width(nm)|resolution(m)|
|---|---|---|---|---|---|---|---|
MSI|	1|	Coastal aerosol|	443.9|	20|	442.3|	20|	60|
MSI|	2|	Blue|	496.6|	65|	492.1|	65|	10|
MSI|	3|	Green|	560.0|	35|	559|	35|	10|
MSI|	4|	Red|	664.5|	30|	665|	30|	10|
MSI|	5|	Vegetation Red Edge	|703.9|	15|	703.8|	15|	20|
MSI|	6|	Vegetation Red Edge|	740.2|	15|	739.1|	15|	20|
MSI|	7|	Vegetation Red Edge|	782.5|	20|	779.7|	20|	20|
MSI|	8|	NIR|	835.1|	115	833|	115|	10|
MSI|	8b|	Narrow NIR|	864.8|	20|	864|	20|	20|
MSI|	9|	Water vapour|	945.0|	20|	943.2|	20|	60|
MSI|	10|	SWIR – Cirrus|	1373.5|	30|	1376.9|	30|	60|
MSI|	11|	SWIR|	1613.7|	90|	1610.4|	90|	20|
MSI|	12|	SWIR|	2202.4|	180|	2185.7|	180|	20|
  
## 4. **产品定义**
  
  
Level-0: 压缩的原始数据。0级产品包含生成1级(及以上)产品级别所需的所有信息。  

Level-1A:级是未经压缩的原始数据，进行了粗略的校正和附加辅助数据。  

Level-1B:辐射校正的辐射亮度数据。物理几何模型使用可用的地面控制点和附加到产品，但不应用。  
  
Note：以上等级数据不向用户分发。

Level-1C:提供正射校正的TOA反射率，亚像素多光谱配准。云和陆地/水面具包括在产品中。  

Level-2A:提供正射校正的BOA反射率，具有亚像素多光谱配准。一个场景分类地图(云，云阴影，植被，土壤/沙漠，水，雪等)包括在产品中。  


  
  
L2A级图像数据产品使用与L1C级相同的tile系统、编码和归档结构。L2A产品以SAFE格式提供，包含以下文件：  
- metadata file (XML file)
- preview image (JPEG2000 with GML geo-location)
- tiles files with BOA reflectances image data file (GML / JPEG2000) for each tile
- datastrip files
- auxiliary data
- ancillary data (GIPPs, set of XML files).  
![img](https://sentinel.esa.int/documents/247904/266422/Sentinel-2_Data_Formats_Figure_1.jpg)
  
每个像素值被编码为12位。2a级场景分类产品格式化输出数据为:
- 60米分辨率的场景分类图
- 雪和云探测。
  
2a级大气校正2a级场景分类产品格式化输出数据为:
- 气溶胶光学厚度(AOT)地图
- 水汽地图
- 表面反射率(BOA)。
在L2A产品中，No Data值表示为0。
[来源](https://sentinel.esa.int/web/sentinel/technical-guides/sentinel-2-msi/level-2a/product-formatting)
  
## 5. **条带系统**
upload shpfile
  
## 6. **预处理程序**
[Sen2Cor](http://step.esa.int/main/snap-supported-plugins/sen2cor)是一款用于以Sentinel-2 Level 1C输入生成Sentinel-2 Level 2A产品的程序。这款程序对L1C级TOA产品执行大气、地形和卷云校正，作为结果，生成BOA，并可选地生成地形和卷云校正图像产品，此外还包括气溶胶光学厚度、水蒸气、场景分类和云和雪的概率图像。其输出产品格式相当于1C级用户产品:JPEG 2000图像，三种不同的分辨率，60米，20米和10米。具体信息参考[Sen2Cor Configuration and User Manual]()。

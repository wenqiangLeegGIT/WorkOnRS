# Landsat Series
---

# **Related Knowledge**  


## 1. About **命名规则**  

规则 `LXSS_LLLL_PPPRRR_YYYYMMDD_yyyymmdd_CC_TX`  
举例 `LC08_L2SP_127031_20150818_20200908_02_T1.tar.gz`  

|名称标识|描述|
|:---:|:---|
|L|Landsat
|X|说明本产品使用何种传感器，如C代表TIRS和OLI
|SS|Landsat系列卫星编号，08代表 landsat 8，09代表 landsat 9
|LLLL|预处理等级，如L2SP(Level 2 Science Product)，L2SR(Level 2 Surface Reflectance) L1GT、L1TP
|PPP|以Worldwide Reference System-2 (WRS-2) 为参考，卫星产品所在path 如128
|RRR|以WRS-2 为参考，卫星产品所在row 如030
|YYYY|影像产品**获取**年份
|MM|影像产品获取月份
|DD|影像产品获取天
|yyyy|影像产品**处理**年份
|mm|影像产品处理月份
|dd|影像产品获取天
|CC|影像产品集合标识(Collection number) 如 C2,C1
|TX|影像产品集合质量分类 ，"T1" 代表Tier 1(质量最优)，"T2" 代表Tier 2，"RT" 代表Real Time


## 2. About **Collection**
2016年，美国USGS将Landsat数据资料重新组织为一个分层（Tier）管理结构，并命名为Collection，这个结构确保所有landsat level1级产品提供已知数据质量的一致存档，同时控制存档的持续改进，并在获取所有数据时访问这些数据，将数据重新组织为Collection 1是landsat 数据档案的一个重要变化，它确保了所有仪器在时间和质量上的一致性，**Collection 1 包含了1972年至今landsat1-8获取的所有一级数据。**  
Landsat Collection 2标志着USGS对landsat level1级别数据档案第二次重大的再处理事件，Collection2利用了近些年来数据处理、算法开发以及数据访问和分发能力方面的最新进展，对几项数据产品进行了显著的改进，Collection 2的一个主要特点是Landsat level 1级数据处理流程中使用的全球地面参考数据集的绝对地理定位精度有了实质性的提高。此外，**Collection 2包括1982年至今更新的DEM建模源、校准和验证更新以及基于全球2级表面反射率和表面温度场景的产品**。  

请注意：基于Landsat Collection 1 的正向处理将持续到**2021年12月31日**，届时，基于Landsat Collection 2的正向处理同时生效。从2022年1月1日起，所有新的landsat数据将仅处理到Landsat Collection 2库存结构中。
鼓励用户在方便的时候尽早将其工作流程迁移到Landsat Collection 2。由于数据处理和算法开发方面的进步，不鼓励用户在同一工作流中交替使用Collection 1和Collection 2。  
Landsat Collection 1停用后，数据仍支持搜索和下载。

## 3. About **Tier**  

按照质量等级排名  
**Tier 1**–OLI/TIRS、ETM+、TM和MSS数据处理至1级精度以及具有图像到图像配准的地形校正产品（L1TP）GLS控制≤12米径向均方根误差（RMSE）。  
**Tier 2**–OLI/TIRS和ETM+数据处理至第1级系统化地形校正产品（L1GT）、TM和MSS数据处理至1级系统校正（L1GS）产品，1级精度和地形校正产品（L1TP），与GLS进行图像对图像注册控制>12米RMSE。  

## 4. About **Level**

- ### **Level 1**  
---
#### **Landsat 8**
Landsat8于**2013年2月11日**发射升空，携带有两个主要载荷：**OLI和TIRS**。其中**OLI（全称：Operational Land Imager ，陆地成像仪）** 由卡罗拉多州的鲍尔航天技术公司研制；
**TIRS（全称：Thermal Infrared Sensor，热红外传感器）**，由NASA的戈达德太空飞行中心研制。设计使用寿命为至少5年。OLI陆地成像仪包括**9个波段**，空间分辨率为**30米**，其中
包括一个15米的全色波段，成像宽幅为185x185km。OLI包括了ETM+传感器所有的波段，为了避免大气吸收特征，OLI对波段进行了重新调整，比较大的调整是OLI Band5(0.845–0.885 μm)，排除了
0.825μm处水汽吸收特征；OLI全色波段Band8波段范围较窄，这种方式可以在全色图像上更好区分植被和无植被特征；此外还有两个新增的波段：蓝色波段 (band 1 0.433–0.453 μm) 主要应用海
岸带观测，短波红外波段(band 9 1.360–1.390 μm) 包括水汽强吸收特征可用于云检测；近红外band5和短波红外band9与MODIS对应的波段接近。TIRS 包括2个单独的热红外波段，分辨率100米。  
Landsat 8 DFCB 中指出，一景完整的landsat 8 L1级产品包含13个文件，其中11个为波段文件，1个元数据文件和1个质量评估文件（BQA）。L1级别产品的命名规`LXSS_LLLL_PPPRRR_YYYYMMDD_yyyymmdd_CC_TX`，其中`LLLL`代表处理等级，通常为以下几种：  
L1TP = Terrain Precision correction，辐射、几何和精度校正，并使用DEM校正因局部地形起伏引起的视差误差；地形校正产品的精度取决于地面控制点（GCP）的可用性以及最佳可用DEM的分辨率。  
L1GT = Systematic Terrain correction，地形校正产品，包括辐射和几何校正，并使用数字高程模型（DEM）校正因局部地形起伏引起的视差误差；地形校正产品的精度取决于最佳可用DEM的分辨率。  
L1GS = geometric systematic correction   
如：LC08_L1GT_029030_20151209_20160131_01_T1

Band Number|Band Description|Band Center(nm)|
|:---:|:---:|:---:|
1|Coastal Aerosol (Operational Land Imager (OLI))|433
2|Blue (OLI)|482
3|Green (OLI)|562
4|Red (OLI)|655
5|Near-Infrared (NIR) (OLI)|865
6|Short Wavelength Infrared (SWIR) 1 (OLI)|1610
7|SWIR 2 (OLI)|2200
8|Panchromatic (OLI)|590
9|Cirrus (OLI)|1375
10|Thermal Infrared Sensor (TIRS) 1|10800
11|TIRS 2|12000

更多信息参见[LANDSAT 8 (L8) LEVEL 1 (L1) DATA FORMAT CONTROL BOOK (DFCB)](https://github.com/wenqiangLeegGIT/WorkOnRS/blob/main/Landsat/LSDS-809-Landsat8-Level1DFCB-v11.pdf)  

---
#### **Landsat 7**

一个完整的landsat 7 level 1 产品包含21个文件，其中9个波段文件，1个元数据文件（MTL.txt），1个GCP文件（GCP.txt），一个README文件包含一个对1级产品内容简要的介绍，9个gap mask文件，并以单独的文件夹存储，分别对应9个波段文件。  
关于`Gap Mask`。2003年5月31日，用于补偿卫星前向运动的扫描线校正器（SLC）失败，并且是永久性的。在没有SLC的情况下，传感器的视线沿着卫星地面轨迹呈之字形。这导致在此日期之后的Landsat 7影像除了中间部分是正常的，影像边缘大部分出现了线状条带的数据缺失情况。gap mask文件为二值文件，0代表缺失，1代表影像数据，每个波段文件都会对应一个gap mask文件。  
更多信息参见[LANDSAT 7 (L7) LEVEL 1 (L1) DATA FORMAT CONTROL BOOK (DFCB)](https://github.com/wenqiangLeegGIT/WorkOnRS/blob/main/Landsat/LSDS-272-Landsat7-Level1DFCB-v19.pdf)
Band Number|Band Description|resolution(m)|
|:---:|:---:|:---:|
1|Blue |30
2|Green |30
3|Red |30
4|Near-Infrared (NIR) (OLI)|30
5|Short Wavelength Infrared (SWIR)|30
6|Thermal(low gain)|60
6|Thermal(high gain)|60
7|Mid-Infrared|30m
8|Panchromatic |10800


#### **Landsat1-5**
landsat 1-5均携带MSS传感器，因此，MSS获取的影像从1972年直至1992年。landsat1,2,3重访周期18天，4,5重访周期16天，并携带了TM传感器。TM传感器波段定义如下    
Band Number|Band Description|wavelength(um)|resolution(m)|
|:---:|:---:|:---:|:---:|
1|Blue |0.45 - 0.52 |30
2|Green |0.52 - 0.60 |30
3|Red |0.63 - 0.69|30
4|Near-Infrared (NIR)|0.76 - 0.90 |30
5|Near-Infrared (NIR)|1.55 - 1.75 |30
6|Thermal|10.40 - 12.50|120
7|Mid-Infrared|2.08 - 2.35 |30

landsat 1-5携带的MSS传感器如下  
Band Number|Band Description|wavelength(um)|resolution(m)|
|:---:|:---:|:---:|:---:|
4|Green|0.5-0.6 |60
5|Red|0.6-0.7 |60
6|Near-Infrared (NIR)|0.7-0.8|60
7|Near-Infrared (NIR)|0.8-1.1|60

- ### **Level 2**
##### **Landsat 8**

Landsat 8 L2 产品文件中包含若干类型影像文件，均为tif格式

- **SR Image Files**  
eg. LC08_L2SP_222005_20140922_20140923_02_T1_SR_B[1-7]{1}.TIF，此类型文件代表1-7波段的Surface Reflectance。
- **ST Image Files**  
eg. LC08_L2SP_222005_20140922_20140923_02_T1_ST_B10.TIF,此文件代表地温产品（Surface Temperature)
- QA Band  
eg. LC08_L2SP_222005_20140922_20140923_02_T1_QA_PIXEL.TIF，此文件为质量控制文件，包含信息丰富，一个重要用途就是用来去除影像中的云。影像数据类型为unsined int16，因此，
每个比特位都包含了特定的信息，如第3位，0代表对应像素点大概率不为云，反之，1则大概率为云。
举例，在某区域的Landsat 8真彩色图像中某一像素为云，同一位置的QA影像像素值为`55052`，转换为二进制数据为`1101011100001100`, 注意从右往左解读，第0位为0，代表是影像数据，第二位为0，原文为`0 for cloud is not dilated or no cloud,1 for cloud dilation`，不是很明白，但不是本次讨论重点，跳过，第三位为1，原文翻译为0代表没有设置卷云置信等级或者是卷云的概率比较低，1则代表是卷云的概率比较高，第四位为1，原文翻译为0代表为云概率低，1则反之，为云的概率较高。剩余比特位代表的信息可直接查询[Data Format Control Book](https://github.com/wenqiangLeegGIT/WorkOnRS/blob/main/Landsat/LSDS-1328_Landsat8-9-OLI-TIRS-C2-L2-DFCB-v6.pdf)第8页。因此我们，可以通过判断第3位比特01状态来判断影像对应像素是否为云。

- **Radiometric Saturation and Terrain Occlusion QA Band & SR Aerosol QA & ST QA**  
参照QA band

- **Metadata**
landsat 系列卫星特有mtl.txt文件，eg. LC08_L2SP_222005_20140922_20140923_02_T1_MTL.[txt,xml] 文件中包含了产品的元数据，非常详细。

- **Angle Coefficient File**
角度信息

- **ST Intermediate Band Files**  
单窗算法计算地温的中间文件，eg. LC08_L2SP_222005_20140922_20140923_02_T1_ST_[TRAD,URAD,DRAD,ATRAN,EMIS,EMSD,CDIST].TIF

更多详细信息参见  [Landsat 8-9 OLI-TIRS Collection 2 Level 2 Data Format Control Book](https://github.com/wenqiangLeegGIT/WorkOnRS/blob/main/Landsat/LSDS-1328_Landsat8-9-OLI-TIRS-C2-L2-DFCB-v6.pdf)


##### **Landsat 4-7**
landsat 4-7的L2级产品大致上与ladnsat8一样，同样包含_SR_B[1-5]波段，代表**经过大气校正**的地面反射率（首先生成表观反射率和亮度温度然后结合辅助数据如水汽饱和度，DEM等采用6S模型得到地面反射率数据），_ST_B6地面温度和地面温度中间数据，以及相应QA质量控制数据。更多信息参见[Landsat 4-7
Collection 2 (C2) Level 2 Science Product (L2SP) Guide](https://github.com/wenqiangLeegGIT/WorkOnRS/blob/main/Landsat/LSDS-1618_Landsat-4-7_C2-L2-ScienceProductGuide-v3.pdf)



### 数据来源
- USGS EarthExplorer https://earthexplorer.usgs.gov/
- Google Earth Engine https://earthengine.google.com/





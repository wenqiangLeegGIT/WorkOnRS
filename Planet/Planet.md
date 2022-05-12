
# Planet
---
# Introduction

Planet公司是世界上在轨卫星最多的公司，共有近200颗在轨卫星，使全球对地观测进入“每日”时代，有着其他公司无法比拟每天覆盖全球一次的超高频时间分辨率。PlanetScope小卫星星座现有在轨卫星共170余
颗，是全球最大的卫星星座，可实现每天监测全球一次。每个PlanetScope卫星成员都是一颗3U立方体（10cm×10cm×30cm）小卫星Dove，Dove航天器均装备一个光学系统和相机，能够拍摄地面分辨率为3~4m的多光
谱影像。并且Dove卫星可以高频率升级和替换，每颗卫星的预期寿命是3年。Dove就像一个扫描仪一样，唯一使命就是为全球提供地球影像数据流。目前Dove卫星已经由第1代升级到第13代，目前已经发射了170余
颗。整个卫星星座有32颗小卫星在国际空间站轨道（ISS）上，140余颗小卫星在太阳同步轨道（SSO）上，全部卫星在太空环绕地球可每日获取整个中国区的卫星影像。
dove和skysat并非单个卫星，都是卫星星座群，均隶属于planet公司，dove星座群是目前在轨数量最大的星座群，可以提供精细时间分辨率和空间分辨率（3m）的多光谱影像，skysat分辨率较高，能够获取全色
0.8可见光1m的影像，两者结合可以研发遥感影像超分辨率模型（参考论文），综合dove影像时间分辨率优势和skysat空间分辨率优势，获取高时间-空间分辨率遥感影像产品。  
* 主站[Planet](https://www.planet.com/)

# Product Info

## Level Defination
Planet影像产品按处理等级分为3级
|名称|描述|等级|
|---|---|---|
|PlanetScope Basic Scene product|Planet 基础图像产品（1B）包括辐射定标后的大气表观反射率图像、辐射定标前的数字量化值（DN）图像及对应的无效数据掩膜文件。数据还包含RPC文件可以供用户进行正射校正处理，适合具有高精度地面控制点的专业用户使用|Level 1B|
|PlanetScope Ortho Scene product|经过正射校正后的大气表观反射率图像或地表反射率图像，包含投影坐标信息。|Level 3B|
|PlanetScope Ortho Tile Product|Planet 瓦片图像产品（3A）是在3B产品的基础上，经过条带拼接和标准正方形格网（25km×25km）裁剪及重采样后的图像产品|level 3A|

## Naming Convention
>\<acquisition date\>_\<acquisition time\>_\<satellite_id\>_\<productLevel\>\<bandProduct\>.\<extension\>   eg. 20200315_023845_95_105a_3B_AnalyticMS_SR.tif
 不是很严格的对应上，但是大概能够明白各项代表的意思
  
## Product Defination
实际应用中多数情况下使用**3B**等级产品，即**PlanetScope Ortho Scene product**，3B产品信息如下：  
|产品属性|描述|
|---|---|
|子产品及格式|1. 影像文件：Geotiff<br>2. 元数据文件：xml<br>3.缩略图文件：Geotiff<br>4.无效数据掩膜(Unusable Data Mask,UDM)：Geotiff<br>5.有效数据掩膜(Usable Data Mask,UDM2)：Geotiff|
|影像朝向|北|
|像素大小(经正射校正)|3m|
|影像位深|可视化图像：8bit<br>Analytic(DN)：12bit<br>可视化图像：8bit<br>Analytic(Radiance - W m-2 sr-1 μm-1)：16bit<br>Analytic SR：16bit|
|影像幅宽|在475km轨道高度上的影像尺寸约为：<br>PS2:25km by 11.5km<br>PS2.SD:25km by 23km<br>PSB.SD:32km by 19.6.5km|
|大气校正|使用6SV2.1辐射传输模型校正进行大气校正，AOD(气溶胶)、水汽、臭氧等输入信息来自MODDIS Near-real-time 数据(MOD09CMA,MOD09CMG,MOD08-D3)|
|地理坐标系|WGS84|
|投影坐标系|UTM|
|重采样方法|Cubic Convlution，三次卷积|
## UDM and UDM2
从2018年8月份开始，全球范围内PSS4波段影像可使用UDM2数据，特定农业区域可追溯至2018年1月。需注意，2018年8月之后，一小部分PSS4波段影像因图像矫正程序失败原因。无法使用UDM2数据。
### UDM (Unusable Data Mask)
udm为**单波段影像**，位深8bit，提供相应影像中不可用数据的相关信息
|Bit|描述|
|---|---|
|0|表示所有影像数据的所有波段中，此像素是否包含blackfill，换言之，是否是有效的数据，1表示blackfill，无数据|
|1|cloud mask,1表示云覆盖，值“1”表示云覆盖率。云检测是在图像的抽取版本（即浏览图像）上执行的，因此很小的云可能会被错过。云区是指在评估波段（红色、NIR或绿色）中像素值高于可配置阈值的区域。有可能会将雪、云阴影、雾霾识别为云。|
|2|标识该区域在影像数据的波段1中是否包含丢失（下行链路期间丢失）或可疑（包含下行链路错误）数据。值“1”表示数据丢失/可疑。如果产品不包括此波段，所有值设置为“0”。|
|3|同bit2解释，但此处波段为2|
|4|同bit2解释，但此处波段为3|
|5|同bit2解释，但此处波段为4|
|6|同bit2解释，但此处波段为5|
|7|目前设置为0|
### UDM2 (Usable Data Mask)
udm2为**多波段影像(8 bands)**，提供了一幅影像中可用数据的信息。各个波段的值是**互斥**的，比如某个像素点分类为云，则不可能是又是其它分类。值为1的像素代表分为此类。
|波段|描述|
|---|---|
|Band1|clear mask,1代表此像素是清晰可用的，0则反之，并且可能为以下5种分类|
|Band2|snow mask,雪掩膜|
|Band3|shadow mask,阴影掩膜|
|Band4|light haze mask,轻度雾霾掩膜|
|Band5|heavy haze mask,重度雾霾掩膜|
|Band6|cloud mask,云掩膜|
|Band7|confidence map,置信度地图，值域0-100，单位percent，从小到大表示对于以上分类可信度|
|Band6|unusable mask,udm|

## Other Info
以下信息从[Planet developer api](https://developers.planet.com/docs/apis/data)中提取，如有需要可以详细阅读。
### About `item` and `assets`
1. 在Planet产品定义中，`item`指的卫星拍摄的逻辑结构上原始颗粒度的数据，可以理解为最初的原始数据，可能经过不同层级的处理，如上面所述1B、3B、3A，assets则是指对item进行处理分析后的数据，偏向应用一些。item中有一个`item_type`属性来表示item所属的类型如`PSScene`/`PSScene3Band`/`PSScene4Band`等，需注意*3/4Band即将在2023年1月弃用，Planet官方推荐PSScene*。


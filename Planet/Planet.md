# Planet
---
# Introduction

Planet公司是世界上在轨卫星最多的公司，共有近200颗在轨卫星，使全球对地观测进入“每日”时代，有着其他公司无法比拟每天覆盖全球一次的超高频时间分辨率。PlanetScope小卫星星座现有在轨卫星共170余
颗，是全球最大的卫星星座，可实现每天监测全球一次。每个PlanetScope卫星成员都是一颗3U立方体（10cm×10cm×30cm）小卫星Dove，Dove航天器均装备一个光学系统和相机，能够拍摄地面分辨率为3~4m的多光
谱影像。并且Dove卫星可以高频率升级和替换，每颗卫星的预期寿命是3年。Dove就像一个扫描仪一样，唯一使命就是为全球提供地球影像数据流。目前Dove卫星已经由第1代升级到第13代，目前已经发射了170余
颗。整个卫星星座有32颗小卫星在国际空间站轨道（ISS）上，140余颗小卫星在太阳同步轨道（SSO）上，全部卫星在太空环绕地球可每日获取整个中国区的卫星影像。
dove和skysat并非单个卫星，都是卫星星座群，均隶属于planet公司，dove星座群是目前在轨数量最大的星座群，可以提供精细时间分辨率和空间分辨率（3m）的多光谱影像，skysat分辨率较高，能够获取全色
0.8可见光1m的影像，两者结合可以研发遥感影像超分辨率模型（参考论文），综合dove影像时间分辨率优势和skysat空间分辨率优势，获取高时间-空间分辨率遥感影像产品。

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

# SMAP (Soil Moisture Active Passive)
---
# Introduction
SMAP（Soil Moisture Active and Passive） 是美国的地球观测卫星之一，**2015年1月31日**发射升空。从名字就可以知道，SMAP主要为了观测土壤水分，并且有主动的传感器和被动的传感器。主动的传感器是L波段雷达，被动的传感器是L波段微波辐射计。计划中，雷达和辐射计各自生产3km和36km的土壤水分产品，并协同生产9km的土壤水分产品。可惜，L波段的雷达当年的7月份（2015年7月7日）就出现了故障，目前SMAP上只有L波段辐射计在孤独地观测着地球。不过，已经有人在研究将SMAP的L波段辐射计数据与欧空局Sentinel的C波段雷达数据结合反演土壤水分，时间分辨率降低了（3天→12天），但空间分辨率由9km提升到了1km[来源](https://www.jianshu.com/p/08aed03bab41)。  

---
# Data Level  
SMAP数据分级如下图所示，主要由两个NASA指定数据中心进行分发，第一个为ASF(Alaska Satellite Facility)，第二个为国家冰雪数据中心(NSIDC,National Snow and Ice Data Center)，ASF专注于SAR数据，NSIDC专注于土地微波数据。ASF提供level1 雷达数据，NSIDC提供level 1 TB 数据和**level2-4**的数据([来源](https://smap.jpl.nasa.gov/data/))。  
**NOTE:由于SMAP L4数据每日更新，因此目前主要使用SMAP来提供土壤湿度数据及其他辅助数据，如气温地温等。**  
![](https://smap.jpl.nasa.gov/internal_resources/520) 


# Data Infomation
SMAP 土壤湿度数据主要包含三个产品，目前主要使用的是Geophysical Data。  
  - Geophysical Data(SPL4SMGP)
  - Analysis Update Date(SPL4SMAU)
  - Land Model Constants(SPL4SMLM)

Geophysical Data(gph)数据包含了一系列3小时平均的*来自同化系统地球物理数据字段(assimilation system ?)*， 例如地表湿度数据。
## File Naming Convention
SMAP_L4_SM_pid_yyyymmddThhmmss_VLMmmm_NNN.[ext]  
eg. SMAP_L4_SM_gph_20150331T013000_Vv6032_001.h5 
  - SMAP: 表示是SMAP数据
  - L4_SM: L4 == level 4 SM == Soil Moisture
  - pid: 产品ID
    - gph Geophysical Data 3小时平均数据，在时间字段T后面的时间是三小时中点，如T013000表示的是某一天00.00.00 到03.00.00的平均数据
    - aup Analysis Update Date 
    - lmc Land Model Constants 
  - yymmddThhmmss: 标示数据的时间  
  - VLMmmm:数据合成ID
    - V Version 版本
    - L launch indicator 发射标示？eg. v:Validated data
    - M 1位数 CRID Major Version Number
    - mmm 3位数CRID Minior version number 
    - eg. **Vv6032** 表示了一个版本为6.032的Validated data 通过[这里](https://nsidc.org/data/smap/data_versions)获取更多关于SMAP数据版本的信息
  - NNN:对于特定日期/时间间隔在相同版本下生成文件的次数，比如002表示2nd time
  - .\[ext\]:文件扩展名
    - h5: HDF5数据
    - qa: Quality Assurance file
    - xml: XML格式的元数据文件
  
  ## Other information
  1. SMAP使用的是**EASE-Grid2.0 Global**投影坐标系，EPSG代码为`6933`，proj4定义为`+proj=cea +lon_0=0 +lat_ts=30 +x_0=0 +y_0=0 +ellps=WGS84 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs`
  2. 空间分辨率9km，时间分辨率1d，时间覆盖从2015年3月31日至今。
 

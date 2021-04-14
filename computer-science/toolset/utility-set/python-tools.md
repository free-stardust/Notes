# 1 气象数据处理
```python
# 程序目的:
#   处理气象出去，获取各个年份气温均值、风速均值和6小时年降水总量；
#
# 其他说明：
#   导入 os 在本程序的目的是遍历所有数据文件；

import os

# 数据文件路径，即每一年气象数据所在文件夹路径
filePath = "E:\\tmp\\data\\china_isd_lite_2019\\"
# 结果文件保存路径
saveFile = "E:\\tmp\\result\\2019_AirTempAve_WindSpeedAve_PrecSum"
# 统计计数，显示处理进度
fileCount = 0

print("Start Processing:")
with open(saveFile, "w") as resultFile:
    for file in os.listdir(filePath):
        fileCount += 1  # 文件计数+1
        siteNum = file[0:6]  # 获取站点编号
        airTempCount = 0  # 统计气温有效值站点数据数量
        windSpeedCount = 0  # 统计风速有效值站点数据数量
        airTempSum = 0.0  # 年气温和
        windSpeedSum = 0.0  # 年风速和
        precipitationSum = 0.0  # 6小时年降水总量
        airTempAve = 0.0  # 年气温均值
        windSpeedAve = 0.0  # 年风速均值
        with open(filePath + file) as dataFile:
            for line in dataFile:
                dataList = line[:len(line) - 1].split()
                if float(dataList[4]) > -9999:  # 排除无效数据
                    airTempCount += 1
                    airTempSum += float(dataList[4])
                if float(dataList[8]) > -9999:  # 排除无效数据
                    windSpeedCount += 1
                    windSpeedSum += float(dataList[8])
                if float(dataList[11]) > 0:  # 排除无效数据
                    precipitationSum += float(dataList[11])
            if airTempCount > 0:  # 如果含有效数据，计算均值
                airTempAve = airTempSum / airTempCount
            else:  # 如果数据无效，赋值-9999
                airTempAve = -9999.0
            if windSpeedCount > 0:  # 如果含有效数据，计算均值
                windSpeedAve = windSpeedSum / windSpeedCount
            else:  # 如果数据无效，赋值-9999
                windSpeedAve = -9999.0
        resultFile.write(str(siteNum) + "\t" +
                         "{:f}".format(airTempAve) + "\t" +
                         "{:f}".format(windSpeedAve) + "\t" +
                         "{:f}".format(precipitationSum) + "\n")
        print(fileCount)
print("Over!")
```
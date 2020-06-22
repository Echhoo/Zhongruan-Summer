# csv & json

## csv

### python的csv模块
> csv: 一系列以逗号分隔的值 

```python
import csv
```

### 使用方法
```python
import csv

filename = 'sitka_weather_07-2014.csv'
with open(filename) as f:
    reader = csv.reader(f)
    header_row = next(reader)       # 表头
    for index, column_header in enumerate(header_row): 
        print(index, column_header)
    """其余数据可以通过阅读文件来阅读，next(reader)可以获取所有数据组成的列表"""
```
表头储存的是每行数据的含义

## json

### python中的json
```python
import json
```

### 使用方法
json.load() 获取一个字典的列表[{}, {}, {}]

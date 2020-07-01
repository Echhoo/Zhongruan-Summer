# Day1

Docker->算力

## 数据
1. 数据获取
   1. 网上统一获取的 -> 不需要处理
   2. 需要处理的，爬的
       - e.g. 评论

2. 数据存储
    1. 文件（hdfs）
       - 分布式文件系统=hdfs
    2. 对于有结构的数据：关系型数据库
    3. 半结构性的数据：HTML、JSON
       1. MongoDB
       2. HBase
       3. Hive

3. 数据处理
   1. 数据获取
   2. 预处理
   3. 数据挖掘=MapReduce（离线批处理） or Spark（在线实时处理）

4. 数据可视化
   - ECharts、matplotlib or ...
# Hadoop

- [Hadoop](#hadoop)
- [Hadoop的I/O](#hadoop的io)
  - [序列化](#序列化)
    - [Writable接口](#writable接口)
    - [Writeable类](#writeable类)
    - [自定义Writeable](#自定义writeable)

# Hadoop的I/O

## 序列化
### Writable接口
```java
package org.apache.hadoop.io;

import java.io.DataOutput; 
import java.io.DataInput; 
import java.io.IOException;

public interface Writable {
    void write(DataOutput out) throws IOException;
    void readFields(DataInput in) throws IOException; 
}
```

### Writeable类
- Writeable的基本Java类封装
    |Java基本类型|Writeable使用|序列化大小（字节）|
    |:-|:-|:-|
    |布尔型|`BooleanWritable`|1|
    |字节型|`ByteWritable`|1|
    |整型|`IntWriteable`|4|
    |整形|`VIntWriteable`|1-5|
    |浮点型|`FloatWriteable`|4|
    |长整型|`LongWriteable`|8|
    |长整型|`VLongWriteable`|1-9|
    |双精度浮点型|`DoubleWriteable`|8|

- Text类

### 自定义Writeable


# matplotlib

## 安装
```
$ pip install matplotlib
```
python中使用
```python
from matplotlib import pyplot as plt
```

## 使用方法
- `plt.plot(x, y, linewidth=)`
    - x: 横坐标
    - y: 纵坐标
    - linewidth: 线宽
- `plt.title(str, fontsize=)`
    - str: 标题内容
    - fontsize: 字体大小
- `plt.xlabel(str, fontsize=)`
    - str: 横坐标的名称
    - fontsize: 字体大小
- `plt.ylabel(str, fontsize=)`
    - str: 纵坐标的名称
    - fontsize: 字体大小
- `plt.tick_params(axis='both', labelsize=)`
    > 设置刻度标记的大小
    - axis: 轴
    - labelsize: 大小
- `plt.show()`
    > 显示绘制的图形
- `plt.scatter(x, y, c=, edgecolor=)`
    > 绘制一个(群)单点的坐标
    - x: 横坐标
    - y: 纵坐标
    - c: 点的颜色
    - edgecolor: 边的颜色
    > 可以为一个列表，对应索引的数值为一个点
- `plt.axis([x_begin, x_end, y_begin, y_end])`
    > 设置坐标的取值范围
- plt.savefig(filename)
    > 保存图片


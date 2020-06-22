# pygal

## 安装
```
$ pip install pygal
```
python中使用
```python
import pygal
```

## 使用方法
- `hist = pygal.Bar()`
    > 声明一个对象
- `hist.title = ""`
    > 改变标题
- `hist.x_labels = ['1', '2']`
    > 横坐标的数值
- `hist.x_title = "Result"`\
   `hist.y_title = "Frequency of Result"`
    > 改变x和y的标题
- `hist.add('', [])`
    > 添加数据
- `hist.render_to_file('die_visual.svg')`
    > **只可以储存到svg文件中！**
    
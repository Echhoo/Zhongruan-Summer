# Echarts

> 主要实现数据可视化

# 五分钟入门
需要提前定义一个`div`用于输出图表
```html
<script type="text/javascript">
        // 基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));

        // 指定图表的配置项和数据
        var option = {
            // 标题相关参数
            title: {
                text: '北京6.14'
            },
            tooltip: {},
            legend: {
                data:['病例数']
            },
            // X 轴
            xAxis: {
                data: ["东城","西城","朝阳","海淀","丰台","石景山","门头沟","房山","通州","顺义","昌平","大兴","怀柔","平谷","密云","延庆","外地来京","境外输入"]
            },
            // Y 轴
            yAxis: {},
            series: [{
                name: '病例数',
                // 指定图表类型
                type: 'bar',
                // 数据对应
                data: [14,55,75,64,78,14,3,18,19,10,29,43,7,0,7,1,25,174,637]
            }]
        };

        // 使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
```

# Echarts基本概念
一个网页可以有多个echarts实例，一个实例可以有多个数据\
以多个数据实例进行绘制（一网页多实例）
- 一网页多实例：多个dom即可

## series

- 系列 包含的要素至少有：一组数值、图表类型（series.type）、以及其他的关于这些数据如何映射成图的参数。
    > 需要包含到options之中
    ![series](../../static/实训/Day4/series-all-a.jpg)

## 组件
![components](../../static/实训/Day4/components.jpg)
多个颜色可以表示多维度的数据

## options
```javascript
// 创建 echarts 实例。
var dom = document.getElementById('dom-id');
var chart = echarts.init(dom);

// 用 option 描述 `数据`、`数据如何映射成图形`、`交互行为` 等。
// option 是个大的 JavaScript 对象。
var option = {
    // option 每个属性是一类组件。
    legend: {...},
    grid: {...},
    tooltip: {...},
    toolbox: {...},
    dataZoom: {...},
    visualMap: {...},
    // 如果有多个同类组件，那么就是个数组。例如这里有三个 X 轴。
    xAxis: [
        // 数组每项表示一个组件实例，用 type 描述“子类型”。
        {type: 'category', ...},
        {type: 'category', ...},
        {type: 'value', ...}
    ],
    yAxis: [{...}, {...}],
    // 这里有多个系列，也是构成一个数组。
    series: [
        // 每个系列，也有 type 描述“子类型”，即“图表类型”。
        {type: 'line', data: [['AA', 332], ['CC', 124], ['FF', 412], ... ]},
        {type: 'line', data: [2231, 1234, 552, ... ]},
        {type: 'line', data: [[4, 51], [8, 12], ... ]}
    }]
};

// 调用 setOption 将 option 输入 echarts，然后 echarts 渲染图表。
chart.setOption(option);
```

## 组件定位
与css类似

## 坐标系
可以两组数据共享X轴
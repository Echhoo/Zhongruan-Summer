# request

## 安装request
```
$ pip install request
```
python中使用
```python
import request

r = request.get(url)
r.status_code               # 获取返回的状态码
response_dict = r.json()    # 获取返回的数据的json形式
```
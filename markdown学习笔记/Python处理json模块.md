
Python处理json模块
========

##python处理json格式模块有json和picle

- json模块提供了四个方法：dumps、dump、loads、load；
- pickle模块也提供了四个功能：dumps、dump、loads、load；
- 序列化：将python的值转换为json格式的字符串；
- 反序列化：将json格式的字符串转换成python的数据类型；

##json与字典相互转换

- json.dumps用于将 Python 对象编码成JSON字符串。
- json.loads将已编码的 JSON 字符串解码为Python 对象
  
```python
import urllib.request
import http.client
import json
#json 转字典
dict_json = json.loads(json_response)
print(dict_json)
print('---------------------------')
# 将字典转换成json字符串
str_json =json.dumps(dict_json)
print(str_json)
```
[^待续]
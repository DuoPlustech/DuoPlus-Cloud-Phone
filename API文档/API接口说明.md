## 准备工作
需要先在控制台的[“自动化”->“API”](https://my.duoplus.cn/api)菜单里面获取API KEY，并在所有API的请求头使用`DuoPlus-API-Key`传入获取到的API KEY。

## 使用限制
每个接口的QPS限制为1

## 请求域名
中国大陆域名：https://openapi.duoplus.cn
非中国大陆域名：https://openapi.duoplus.net

## 请求方式
POST

## 请求头

| 参数 | 值 | 说明 |
| - | - | - |
| Lang | zh | 设置接口交互语言，支持：zh，zh-TW，en，ru |
| Content-Type | application/json | 全部使用JSON进行传递 |
| DuoPlus-API-Key | xx-xx-xx | API Key，在控制台的“自动化”->“[API](https://my.duoplus.cn/api)”菜单里面获取 |

## 请求参数
使用JSON字符串传递
```json
{"key":"value"}
```

## 返回参数
| 参数 | 类型 | 说明 |
| --- | --- | --- |
| code | int | 响应状态码，200为正常；401需重新登录 |
| data | object | 内容体 |
| message | string | 信息，一般为错误信息 |

## 分页说明
#### 分页请求参数

| 参数 | 类型 | 必需 |  说明 |
| --- | --- | --- | --- |
| page | int | 否 | 请求页码，若不传则默认为第一页 |
| pagesize | int | 否 | 每页数量，若不传则后端默认10条/页 |

#### 分页返回参数
> 以下参数在返回值data对象里面，一般对于列表，data里面有list以及同级的下面分页参数

| 参数 | 类型 | 必需 |  说明 |
| --- | --- | --- | --- |
| page | int | 是 | 第几页 |
| pagesize | int | 是 | 每页数量 |
| total | int | 是 | 总条数 |
| total_page | int | 是 | 总页码 |

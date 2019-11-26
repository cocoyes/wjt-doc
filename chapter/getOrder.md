# 查询订单状态
---

## 新版接口
#### HTTP请求


GET		/common/getOrder

#### 请求参数

| 参数名    | 类型   | 说明                                             |
| --------- | ------ | ------------------------------------------------ |
| orderId   | string | 应用方订单号                                 |
| appId     | string | 应用id |

#### 响应示例

``` json
{
    "data": {
        "token": "ETH",
        "appId": "1007",
        "orderId": "381714415147286528",
        "toAddress": null,
        "state": 3,
        "createDate": "2019-11-20 16:17:39",
        "num": 17.8063,
        "realCoinNum": 16.02567,
        "mark": "商品支付"
    },
    "code": 0,
    "message": "成功",
    "total": null
}
```
响应说明：data部分state状态分别表示：

``` lsl
0	初始化
1	等待支付
2	支付未完成
3	完成支付
4	支付失败
5	超额支付
```

  
## 旧版接口
#### HTTP请求


GET		/common/getOrderStatus

#### 请求参数

| 参数名    | 类型   | 说明                                             |
| --------- | ------ | ------------------------------------------------ |
| orderId   | string | 应用方订单号                                 |
| productId     | long | 应用id |

#### 响应示例

``` json
{
    "data": {
        "token": "ETH",
        "appId": "1007",
        "orderId": "381714415147286528",
        "toAddress": null,
        "state": 3,
        "createDate": "2019-11-20 16:17:39",
        "num": 17.8063,
        "realCoinNum": 16.02567,
        "mark": "商品支付"
    },
    "code": 0,
    "message": "成功",
    "total": null
}
```
响应说明：data部分state状态分别表示：

``` lsl
0	初始化
1	等待支付
2	支付未完成
3	完成支付
4	支付失败
5	超额支付
```



# 打开H5跳转网页
---


#### HTTP请求


GET		/common/openMyCoin

#### 请求参数

| 参数名    | 类型   | 说明                                             |
| --------- | ------ | ------------------------------------------------ |
| backUrl   | string | 成功后的会跳地址                                 |
| token     | string | 下单接口返回的data值，有效时间10分钟，请尽快使用 |
| productId | long   | 与appId同值，应用id                              |
| symbol    | string | 币单位，例如BTC、ETH                             |


打开网页后，网页自动拉起app进行支付。个别浏览器会阻止网页与应用通信！

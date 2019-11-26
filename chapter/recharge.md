# 发起充值
---
注意：该接口需要签名。

## 通过H5拉起支付的下单方式

#### HTTP请求

``` stata
Content-Type:application/json
POST	/chainPay/sendOrder
```
#### 请求参数

| 参数名                           | 类型   | 说明                                                                                                                        |
| -------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------- |
| appId                            | string | 应用ID，例如1001                                                                                                            |
| appKey                           | string | 应用key，例如ee1a7aec56a1e1990ca1024ac4f3533569                                                                             |
| messageId                        | string | 消息id,没做要求，可重复，可随机                                                                                             |
| modType                          | int    | 应用类型(0联网、1单机)                                                                                                      |
| orderId（联网）deviceId（单机） | string | 联网应用请填参数名orderId，单机应用请填deviceId。注意：为避免单机应用需要后期进行支付，请在应用设备号加随机字符，防止重复订单 |
| num                              | string | 充值数量  
| token                              | string | 充值指定币种单位，例如BTC、ETH，可以不指定（强烈推荐指定币种）|
| mark                             | string | 备注说明                                                                                                                    |
| sign                             | string | 签名                                                                                                                        |

请求JSON示例：  

``` json
{
	"appId": "1007",
	"appKey": "045d7a45cc7f9f2c0b73f5c818a8b2b4",
	"messageId": "1000001",
	"modType": 0,
	"params": {
		"num": "55",
		"mark": "测试",
		"orderId": "2019112502201",
		"token": "BTC"
	},
	"sign": "BE6146C821CECCF1E843C96EB97A66CC"
}
```
#### 响应示例

``` json
{
    "code": 0,
    "message": "success",
    "data": "035bac504a0c4fd183242e496bb27f02",
    "totalPage": null,
    "totalElement": null
}
```
返回值data部分作为打开H5网页时传递的参数值。  









  
    
	  
	    

## 通过app通信拉起支付的下单方式

这是一个会返回app 通信参数的下单接口  
#### HTTP请求

``` stata
Content-Type:application/json
POST	/chainPay/sendOrderByH5
```
#### 请求参数

| 参数名                           | 类型   | 说明                                                                                                                        |
| -------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------- |
| appId                            | string | 应用ID，例如1001                                                                                                            |
| appKey                           | string | 应用key，例如ee1a7aec56a1e1990ca1024ac4f3533569                                                                             |
| messageId                        | string | 消息id,没做要求，可重复，可随机                                                                                             |
| modType                          | int    | 应用类型(0联网、1单机)                                                                                                      |
| orderId（联网）deviceId（单机） | string | 联网应用请填参数名orderId，单机应用请填deviceId。注意：为避免单机应用需要后期进行支付，请在应用设备号加随机字符，防止重复订单 |
| num                              | string | 充值数量  
| token                              | string | 充值指定币种单位，例如BTC、ETH，可以不指定（强烈推荐指定币种）|
| mark                             | string | 备注说明                                                                                                                    |
| sign                             | string | 签名                                                                                                                        |

请求JSON示例：  

``` json
{
	"appId": "1007",
	"appKey": "045d7a45cc7f9f2c0b73f5c818a8b2b4",
	"messageId": "1000001",
	"modType": 0,
	"params": {
		"num": "55",
		"mark": "测试",
		"orderId": "2019112502201",
		"token": "BTC"
	},
	"sign": "BE6146C821CECCF1E843C96EB97A66CC"
}
```
#### 响应示例

``` json
{
    "data": {
        "productName": "商城",
        "productIcon": "https://www-alphagdax-com.oss-cn-zhangjiakou.aliyuncs.com/2019/09/03/f4d960f5-793d-473d-bada-b228bd3510f1.png",
        "productId": 1007,
        "orderId": "2019112502201",
        "token": null,
        "coinPriceVos": [
            {
                "coinNo": 1,
                "coinCore": "ETH",
                "coinName": "ETH",
                "rmbPrice": null,
                "dollarPrice": null,
                "price": 55,
                "address": "0x71ae3a8a8fa8f3ac93d1997535d4b37083e8f690"
            }
        ],
        "payAppInfo": {
            "id": 1,
            "appName": "无界通",
            "appUrl": "https://app.agdax.top/?id=45",
            "appIosUrl": "clickstarcoin://mycoin3/mypath?scanContent=",
            "appIcon": "https://app-biaoshop-cn.oss-cn-zhangjiakou.aliyuncs.com/soft/20191108203943_198058.png",
            "appClickUrl": "clickmycoin://mycoin3/mypath?scanContent=",
            "appIosClickUrl": "clickmycoin://testcoin/mypath?scanContent=",
            "faceUrl": "http://www.alphagdax.com"
        }
    },
    "code": 0,
    "message": "success",
    "total": null
}
```
请根据返回参数信息，主动拉起app进行支付。
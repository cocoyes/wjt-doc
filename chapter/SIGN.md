# 签名方式说明
---
签名方式：MD5字符串签名。

## Demo程序
如果您觉得以下说明太复杂、看不懂、难以理解，我们提供了接口接入的demo程序。  

 1. JAVA版Demo程序  

## 签名方式
我们将需要需要进行签名的参数归为两种类型，1、必要参数		2、常规参数
必要参数通常由您的appId、appKey构成（请勿将私钥appPrivateKey放进来了）的验证类参数，常规参数则为调用该接口所需要的功能性参数，这里统称为params。
params是一个Map对象，里面存放多个常规参数。例如orderId、num、token等均放入params内。  
签名的顺序为：将appId、appKey、params里面的参数名以 字典升序 进行排列，将参数的值按参数名排列的顺序进行拼接，最后将您的私钥（appPrivateKey）追加在最后，然后进行MD5签名即可，最终的签名sign值，请转为大写。
例如，我们有如下参数名、参数值对应关系：  

``` makefile
appId = 1001
appKey = 51f0cc7f3a2d3e52129c8b9c0d09450e
messageId = 1000001
modType = 0
```
params内参数：

``` makefile
num = 2
mark = 测试
orderId = 20191125001
```

私钥为appPrivateKey = aa1a7aec56a1e1990ca1024ac4f3533569  
则经过参数名的升序排列后，参数顺序如下：

``` stylus
appId appKey mark num orderId   
```

参数值拼接情况如下：

``` llvm
100151f0cc7f3a2d3e52129c8b9c0d09450e测试220191125001aa1a7aec56a1e1990ca1024ac4f3533569
```
<i class="far fa-bell"></i>请注意，messageId和modType 不需要参与签名  

此时，我们只需要将appPrivateKey的值追加在上面一长串字符的后面即可，然后进行MD5签名并转为大小即完成签名。  
签名参数为sign。

以充值为例，此时请求充值接口需要提交的json值如下：

``` json
{
	"appId": "1001",
	"appKey": "51f0cc7f3a2d3e52129c8b9c0d09450e",
	"messageId": "1000001",
	"modType": 0,
	"params": {
		"num": 2,
		"mark": "测试",
		"orderId": "20191125001"
	},
	"sign": "90FB59CDA1BE1679E5CF071A08DF6EA8"
}
```

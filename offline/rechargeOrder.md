# 服务商平台-手续费充值

**简要描述：** 
- 服务商可以通过该接口，对商户手续费账户进行充值。

**请求URL：** 
- 服务商->联动优势
`{交易服务根地址}/pay/rechargeOrder`

**请求方式：**
- POST 

**请求参数：** 

|	字段	 |	名称	  |	长度  	|	必填  	|	说明	  |
|:--------:|:--------:|:--------:|:--------:|:--------|
|	acqSpId	|	代理商编号	|	10	|	M	|	代理商编号(联动平台分配)	|
|	acqMerId	|	商户号	|	8	|	M	|	商户号(联动平台分配)	|
|	orderDate	|	订单日期	|	8	|	M	|	订单日期，格式yyyyMMdd	  |
|	orderNo	|	充值订单号	|	32	|	M	|		  |
|	amount	|	充值金额	|	13	|	M	|	单位分	  |
|	bankType	|	银行卡类型	|	1	|	M	|	0：个人借记卡 4：对公账户	  |
|	bankShortName	|	银行简称	|	4	|	M	|		  |
|	notifyUrl	|	通知地址	|	128	|	M	|	充值结果后台通知地址	  |
|	signature	|	签名	|	256	|	M	|	参见签名机制	|

 **商户请求报文示例**

```json
{
	"acqMerId":"42524496",
	"acqSpId": "Y471790403",
	"amount":"100",
	"bankShortName":"CMBC",
	"bankType":"0",
	"notifyUrl":"http://www.bi.com/NotifyWeb/DemoGetNot",
	"orderDate":"20200914",
	"orderNo":"JD202009140445350001",
	"signature":"Y0m+jRve0nso4x2O3GU38KX5JzpuBnAgbqieBNop2ScTqbrb6Dwhm2tfG/eU2M7OUJvAB3JeLesVVTD5Eh1LoxHcMtI5iaLPdW5bDDzeSFN1trGm9GFbuxebyrUzPSnPN1HAPTAZlmSMUArhHLJ5bp+wAm8gl37EtQLScBWlnRw="
}
```

 **返回参数说明** 
 

|	字段	|	名称	|	长度	|	必填	|	说明	|
|--------|--------|--------|--------|--------|
|	respCode	|	返回码	|	变长8	|	M	|	返回码	|
|	respMsg	|	返回信息	|	变长128	|	M	|	返回信息	|
|	funCode	|	功能码	|	变长8	|	M	|	定值：020120	|
|	rpid	|	会话流水	|	变长20	|	M	|	会话流水	|
|	reqDate	|	请求日期	|	定长8	|	M	|	yyyyMMdd	|
|	reqTime	|	请求时间	|	定长8	|	M	|	HHmmss	|
|	instId	|	机构号	|	定长8	|	M	|	机构号	|
|	trace	|	机构流水号	|	定长16	|	M	|	机构流水号	|
|	payAmt	|	支付总金额	|	变长13	|	M	|	单位分，充值金额+手续费	|
|	comAmt	|	充值手续费	|	变长13	|	M	|	充值手续费	|
|	binBankId	|	发卡行	|	变长4	|	M	|	发卡行	|
|	productId	|	产品号	|	变长8	|	M	|	产品号	|
|	bankCardType	|	银行卡类型	|	定长1	|	M	|	0-个人借记卡  4-对公账户	|
|	sign	|	支付签名信息	|	变长128	|	M	|	支付签名信息	|
|	notifyUrl	|	后台通知地址	|	变长128	|	M	|	网银网关通知联动上账的地址	|
|	version	|	支付版本信息	|	定长3	|	M	|	支付版本信息	|
|	expand	|	扩展信息	|	变长128	|	M	|	结算集合	|
|	payUrl	|	充值地址	|	变长128	|	M	|	请求网银网关的地址	|
|	orderNo	|	充值订单号	|	变长32	|	M	|	充值订单号	|




 **返回报文示例**

```json
{
    "respCode":"00",
    "respMsg":"处理成功",
    "signature":"OA2DUC5aT3Uwp9de4VHNKoW8CLvZ6piUWOEYyXuBsktEp2I7iaOZTFnOwgjrPVM8cDFaWN3qHBt1R+mN7nvrSZ4R7EtsbgDFMWgKAE8gNQCsUsPvjqpqUIc4+JVUaxLv/nhd2yt08/au07A/oDLIw5PJZdH8Vtf9zRUfmY9su/Y=",
    "funCode":"020120",
    "rpid":"P08453975462460",
    "reqDate":"20200914",
    "reqTime":"164522",
    "instId":"30000003",
    "trace":"2009147645397871",
    "acqMerId":"42524496",
    "payAmt":"101",
    "comAmt":"1",
    "binBankId":"B008",
    "productId":"P15100H2",
    "bankCardType":"12",
    "sign":"nQvVltuaW8ZXRr4NhImJjs4/neef5Xd6WzeBBdkihraA0HQ0LY29aCDdGZlJ7vP+IhSUkrkbuwLlAWZwyvmetx+hW/jRgG+dPCehs77tRHkQ2tqCMhAG8RkmUv0tW66ob2fxrUXK6gWwy458GIFqWrI1PyjsSaltE1ULAE4RTSU=",
    "retUrl":null,
    "notifyUrl":"http://10.10.178.157:6904/recharge/backNotify",
    "version":"2.0",
    "expand":"merId:NDI1MjQ0OTY=;orderId:MjAwOTE0NzY0NTM5MjcwMQ==",
    "payUrl":"http://10.10.178.75:8082/ebankpay/recvOrder.htm",
    "orderNo":"JD202009140445350001"
}
```



**网银支持银行** 

|	序号	|	发卡行简称	|	发卡行名称 |	描述	|
|--------|--------|--------|--------|
|	1	|	BOC	|	中国银行	|		|
|	2	|	ABC	|	中国农业银行	|		|
|	3	|	ICBC	|	中国工商银行	|		|
|	4	|	CCB	|	中国建设银行	|		|
|	5	|	COMM	|	交通银行	|		|
|	6	|	PSBC	|	中国邮政储蓄银行	|		|
|	7	|	CMB	|	招商银行	|		|
|	8	|	CMBC	|	中国民生银行	|		|
|	9	|	CITIC	|	中信银行	|		|
|	10	|	CEB	|	中国光大银行	|		|
|	11	|	HXB	|	华夏银行	|		|
|	12	|	GDB	|	广发银行	|		|
|	13	|	CIB	|	兴业银行	|		|
|	14	|	SPDB	|	上海浦东发展银行	|		|
|	15	|	BJB	|	北京银行	|	仅支持银行卡类型bankCardType为0-个人借记卡	|
|	16	|	SPAB	|	平安银行	|	仅支持银行卡类型bankCardType为0-个人借记卡	|





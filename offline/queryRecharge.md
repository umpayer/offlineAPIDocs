# 服务商平台-充值订单查询

**简要描述：** 
- 服务商可以通过该接口，查询商户充值的状态。

**请求URL：** 
- 服务商->联动优势
`{交易服务根地址}/pay/queryRechargeOrder`

**请求方式：**
- POST 

**请求参数：** 

|	字段	 |	名称	  |	长度  	|	必填  	|	说明	  |
|:--------:|:--------:|:--------:|:--------:|:--------|
|	acqSpId	|	代理商编号	|	10	|	M	|	代理商编号(联动平台分配)	|
|	acqMerId	|	商户号	|	8	|	M	|	商户号(联动平台分配)	|
|	orderDate	|	订单日期	|	8	|	M	|	订单日期，格式yyyyMMdd	  |
|	orderNo	|	充值订单号	|	32	|	M	|		  |
|	signature	|	签名	|	256	|	M	|	参见签名机制	|

 **商户请求报文示例**

```json
{
	"acqMerId":"43645565",
	"acqSpId":"Y251150345",
	"orderDate":"20200915",
	"orderNo":"JD202009151008370001",
	"signature":"Iq92curAo3eOQEpSc75Qgu/LK6XjxGJGx/V2LAIUrw5sMh8aaWfaBulg0K/l+AvC9VrglJN1p2haxfMOd/k2q3K85/kGXiqCvpB6ecNal2PTv8S/psobNroVphgSEPc2HGWD4ZoQL3nQ92poobl2Zs1Ohv9sgHehwn4DIyZYoR0="
}
```

 **返回参数说明** 
 
 一级字段说明

|	字段	|	名称	|	长度	|	必填	|	说明	|
|--------|--------|--------|--------|--------|
|	respCode	|	返回码	|	8	|	M	|	返回码	|
|	respMsg	|	返回信息	|	128	|	M	|	返回信息	|
|	acqSpId	|	代理商编号	|	10	|	C	|	代理商编号(联动平台分配)	|
|	acqMerId	|	商户号	|	8	|	C	|	商户号(联动平台分配)	|
|	orderNo	|	充值订单号	|	32	|	C	|	充值订单号	|
|	orderDate	|	订单日期	|	8	|	C	|	订单日期		|
|	comAmt	|	充值手续费	|	13	|	C	|	单位分	|
|	amount	|	充值金额	|	13	|	C	|	单位分	|
|	tradeState	|	订单状态	|	1	|	C	|	0：等待支付 7：充值失败 8：充值成功	|
|	signature	|	签名信息	|	变长128	|	C	|		|




 **返回报文示例**

```json
{
    "respCode":"00",
    "respMsg":"处理成功",
    "signature":"UEpOR8tHC5VW059s6NU2Gz0bcpQjbMg1rffYk0jo7eWgvogOPFKLbBVP0YEbw/8ff9QUSb+zVNwkJB95dN6I9kHleeKplzUP4LCpriT1G4vuJSnDvIjo7f18E4N0PoLDCJK6LA1kb+jFaiuPnjg6iWeYa/50XCsBDoaDt6u8pBA=",
    "acqSpId":"Y251150345",
    "acqMerId":"43645565",
    "orderNo":"JD202009151008370001",
    "orderDate":"20200915",
    "comAmt":"1",
    "amount":"100",
    "tradeState":"0"
}
```








# 服务商平台-单笔付款接口

**简要描述：** 
- 服务商可以通过该接口，根据账户余额，进行部分金额结算能力。

**请求URL：** 
- 服务商->联动优势
`{交易服务根地址}/pay/revPay

**请求方式：**
- POST 

**请求参数：** 

|	字段	 |	名称	  |	长度  	|	必填  	|	说明	  |
|:--------:|:--------:|:--------:|:--------:|:--------|
|	acqSpId	|	代理商编号	|	10	|	M	|	代理商编号(联动平台分配)	|
|	acqMerId	|	商户号	|	8	|	M	|	商户号(联动平台分配)	|
|	trace	|	商户订单号	|	64	|	M	|		  |
|	txnAmt	|	交易金额	|	13	|	M	|	是人民币，且以分为单位 |
|	signature	|	签名	|	256	|	M	|	参见签名机制	|

 **商户请求报文示例**

```json
{
	"acqMerId": "41509208",
	"acqSpId": "Y471790403",
	"trace": "HSAPI1520909695265",
  "txnAmt": "1",
	"signature": "TJ1Ibz5jkLMVnWRw4TCbasm8y1OQWaYe9pvv95Y/KTt3o++dQ97/eimWkHin8yUsZtHbzNGkT7l0tZCZ0EY/oBBRzftp6qPGa0kSj/vVrq/sfUJccgfwpSwuhdW1Zwiy/M/hudtTc4u3taeTjekYwnuZSpEnvGPXF4GNhFFPT4o="
}
```

 **返回参数说明** 

 一级字段说明

|	字段	|	名称	|	长度	|	必填	|	说明	|
|--------|--------|--------|--------|--------|
|	respCode	|	返回码	|	8	|	M	|	返回码	|
|	respMsg	|	返回信息	|	128	|	M	|	返回信息	|
|	signature	|	签名	|	256	|	M	|	参见签名机制	|

 **返回报文示例**

```json
{
    "respCode": "00",
    "respMsg": "处理成功",
    "settleTime": "20200811100000",
    "settleAmt": "100000",
    "settleComAmt": "25",
    "signature": "lkD1PuEv/tb+f1JNWRAC8EHIStWi/smtpCZBXRYwbHJsO4Rt+wzNMtal4apAqvQqH8hVgJLJF7OxLby4pwTdfcbAfuOJQ8MR4K8oWoBXkeLIFKQJhSda3qqxHtZBVz5d0OGsqxgdNs0oSIC44W5Ep2TXkTGcopDfi8K+mi2v5es=",
 }
```



**备注** 

- 返回码为：00，表示结算成功。其他返回码为失败，具体原因可以咨询对接人员排查。


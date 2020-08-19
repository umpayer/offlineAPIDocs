# 服务商平台-pos预下单查询接口
    
**简要描述：** 

- pos机器查询联动平台获取用户最新下单信息，继续后续支付操作。

**请求URL：** 
- 服务商->联动优势
`{交易服务根地址}/pay/preorderQuery`
  
**请求方式：**
- POST 

**请求参数：** 


|	字段	 |	名称	  |	长度  	|	必填  	|	说明	  |
|:--------:|:--------:|:--------:|:--------:|:--------|
|	acqSpId	|	代理商编号	|	10	|	M	|	代理商编号(联动平台分配)	|
|	acqMerId	|	商户号	|	8	|	M	|	商户号(联动平台分配)	|
|	modelId	|	终端型号编号	|	32	|	M	|	终端型号编号	|
|	signature	|	签名	|	256	|	M	|	参见签名机制	|

 **商户请求报文示例**

```json

{
  "acqSpId": "Y000000001",
  "acqMerId": "30000064",
	"signature": "CBr2Dui55aRxyiUJoWCxckL8lWn7UeBxvAJFsV2hrtFDvVSOp4v4cgUPc1Nk3e1d+oitAhi9b3AAVSoAuEWV0fKKIQRwYTSPTzLbX9fLXq2KE423Km5GW5HWqpN8+guCH1UUpSlNVzVYax9h5D/n2YSWv/g6KWZYye+kEP8K3rA="
}

```

 **返回参数说明** 
 
|	字段	|	名称	|	长度	|	必填	|	说明	|
|--------|-------|--------|--------|--------|
|	respCode	|	返回码	|	8	|	M	|	返回码	|
|	respMsg	|	返回信息	|	128	|	M	|	返回信息	|
|	acqSpId	|	代理商编号	|	10	|	M	|	代理商编号(联动平台分配)	|
|	acqMerId	|	商户号	|	8	|	M	|	商户号(联动平台分配)	|
|	transactionId	|	联动交易流水号	|	32	|	M	| 联动交易流水号	|
|	txnAmt	|	订单金额	|	13	|	M	|	单位:分	|
|	payType	|	支付方式	|	12	|	M	|	BankCard:刷卡<br> BarCode：被扫<br> Native：主扫	|
|	orderType	|	订单类型	|	12	|	O	|	AL-支付宝 <br> WX-微信支付 <br> BC-银联二维码	|
|	payVoucher	|	付款凭证号	|	6	|	M	|	posp下单流水号	|
|	signature	|	签名	|	256	|	M	|	参见签名机制	|

**备注** 

- 返回码（00）为成功，继续后续支付操作。
- 返回码为其他表示失败，请重新查询。其中17为：没找到待支付订单

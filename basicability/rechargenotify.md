# 充值结果通知

**简要描述：** 
- 联动优势把充值成功结果同步通知给服务商
- 联动优势最多通知商户4次，如果商户未收到交易结果，平台则会在30秒左右再通知一次，如再次失败，平台会再通知两次，每次将间隔10分钟将交易结果重发给商户

**请求URL：** 
- 联动优势->服务商
`{商户接收通知地址}`以充值下单时传入的通知地址{notifyUrl}为准

**请求方式：**
- POST 

**请求参数：** 

|	字段	 |	名称	  |	长度  	|	必填  	|	说明	  |
|:--------:|:--------:|:--------:|:--------:|:--------|
|	acqSpId	|	代理商编号	|	10	|	M	|	代理商编号(联动平台分配)	|
|	acqMerId	|	商户号	|	8	|	M	|	商户号(联动平台分配)	|
|	orderDate	|	订单日期	|	8	|	M	|	订单日期，格式yyyyMMdd	  |
|	orderNo	|	充值订单号	|	32	|	M	|	商户唯一订单号	  |
|	amount	|	付款金额	|	13	|	M	|	以“分”为单位,付款转账金额。（实际扣款金额为付款金额加手续费）	  |
|	comAmt	|	手续费金额	|	13	|	C	|	付款的手续费，金额以分为单位	  |
|	transferDate	|	付款日期	|	32	|	C	|	付款完成的日期，格式是yyyyMMdd	  |
|	comAmtType	|	手续费承担方	|	32	|	C	|	-99手续费从银行卡中扣除	  |
|	tradeState	|	交易状态	|	1	|	M	|	8：充值成功	  |
|	version	|	版本号	|	3	|	M	|	定值4.0	  |
|	sign	|	签名	|	256	|	C	|	参见签名机制	|

 **商户请求报文示例**

```application/x-www-form-urlencoded
{
	"acqMerId": "30000102",
	"acqSpId": "Y000000001",
	"orderNo": "JD202009150206470001",
	"orderDate": "20200915",
	"amount": "1",
	"comAmt": "0",
	"transferDate": "20200915",
	"comAmtType": "-99",
	"tradeState": "8",
	"sign": "lyaVkCr8oHqCzYHPDbpFWTlmBK2ok3nw1mkNWQUTggoX1FTMaZfVSkdb1BJu9IYc3e59b6zH6jF4fATanZRPE72WDg0wL2TxkWxih7rXHCAPSux9VlQWVDr4GSwODU+hvbZf6DLOUJehxJfenWpTa9/pMborIJ45Lx6zEAmX06o="
}
```

 **返回参数说明** 
 
| 字段      | 名称     | 长度 | 必填 | 说明                                 |
| --------- | -------- | ---- | ---- | ------------------------------------ |
| respCode  | 返回码   | 8    | M    | 00：收到通知<br />其他：继续重复通知 |
| respMsg   | 返回信息 | 128  | M    | 返回信息                             |
| signature | 签名     | 256  | M    | 参见签名机制                         |




**接收说明**

【接收格式】HTTP   POST

【接收示例】servlet（JAVA版本）

```java
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		System.out.println("*************************【param接口】收到POST请求信息***start**************************");
        //解析接收到参数
		System.out.println("**【param数据】*********start***********");
		Enumeration<String> en = request.getParameterNames();
		while(en.hasMoreElements()) {
			String key = en.nextElement();
			System.out.println("**【param数据】[key]=["+key+"]  [value]=["+URLDecoder.decode(request.getParameter(key))+"]");
		}
		System.out.println("**【param数据】*********end***********");
        //解析组织返回参数
		JSONObject json = new JSONObject();
		json.put("respCode", "00");
		json.put("respMsg", "收到");
		response.setContentType("application/json; charset=utf-8");
		System.out.println("**【json数据】回复响应结果："+JSONUtil.toJsonStr(json));
	    response.getWriter().write(JSONUtil.toJsonStr(json));
		System.out.println("*************************【param接口】收到POST请求信息***end**************************");
	}                                                                                                                          
```








# 服务商平台-对账文件

**简要描述：** 

- 联动优势内部生成
- 每天早8点生成前一日的对账文件


**对账文件名称：**

- 服务商 ID_日期.csv, 如: Y123456789_20181207.csv 

**对账文件数据：**

|    字段名    |      描述      | 
| :----------: | :------------: | 
| 商户订单号   |   服务商传入的当笔订单(或退款单)的订单号。   |
| 交易时间     |    当笔订单(或退款单)的支付成功时间, 格式为 YYYYMMDDHHMMSS,如 20180729100000    |
| 商户代码     |    联动分配的商户号    |
| 终端号       |    当笔交易对应的终端号,联机交易不传时留空。    |
| 商户门店编号 |    当笔交易对应的门店编号,联机交易不传时留空。    |
| 操作员编号   |    当笔交易对应的操作员编号,联机交易不传时留空。    |
| 商户名称     |    当笔交易对应的商户名称。    |
| 联动订单号   |    联动侧订单号    |
| 卡属性  	   |    银行卡卡类型：01 – 借记卡；02 – 贷记卡(含准贷记 卡)     |
| 交易状态     |    SUCCESS – 支付成功; REFUND – 退款成功；FAILED – 交易失败。    |
| 订单金额     |    该笔订单的初始交易金额,单位为分。 当笔订单为 退款单时,本字段填 0     |
| 退款金额     |    服务商申请退款的金额,单位为分。 当订单为支付订单时,本字段填 0。     |
| 订单类型     |     alipay – 支付宝；wechat – 微信支付；unionpay – 银联二维码；mobilepos-手机pos；bankcard-银行卡收单     |
| 支付场景     |    1 – 主扫支付；2 – 被扫支付；3 – 微信公众号、支付宝服务窗支付小程序支付；4 – 银联JS支付     |
| 商户手续费   |    单笔交易收取商户手续费的金额,单位为分     |
| 商户费率（%）|    商户费率（%）     |
| 结算方式     |    单笔交易结算方式，T1、D1等     |
| 结算金额     |    单笔交易结算金额，单位为分     |
| 附加费率（%）|    附加费率（%）     |
| 附加手续费   |     附加手续费，单位为分     |
| 联动流水号   |    联动流水号     |
| 第三方流水号 |    微信、支付宝流水号     |
| 订单类型     |   消费订单、分账订单     |
| 商户分账订单号 |    商户分账订单号    |
| 联动分账流水号 |    分账订单子订单号     |
| 分账商户      |    分账商户号     |
| 分账退款账户类型 |    现金账户、担保账户     |
| 参考号 |    参考号     |

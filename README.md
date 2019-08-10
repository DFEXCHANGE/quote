# dfex行情接口

1.获取所有上线的币种

2.获取交易对实时行情

3.获取交易对最新深度

4.获取交易对成交列表



接口访问域：

www.dfex.com/polarisex

0. 接口统一返回格式

    | 字段名 | 数据类型 | 说明 |
    | --- | --- | --- |
    | attachment | object | 接口数据 |
    | status | int | 接口状态成功显示200 |
    | message | string | 描述 |
   
    
1. 获取所有上线的币种
    - 请求方式：GET
    - url：`https://{host}/quote/public/`
    - 示例：https://www.dfex.com/polarisex/quote/public
    - 传入值：空
    - 返回值data信息：
    
    | 字段名 | 数据类型 | 说明 |
    | --- | --- | --- |
    | id | int | 唯一标识 |
    | last | string | 最新成交价 |
    | lowestAsk | string | 卖一价 |
    | highestBid | int | 买一价 |
    | percentChange | string | 24小时涨跌幅 |
    | quoteVolume | string | 24小时成交量 |
    | isFrozen | string | 是否冻结 默认都为0 |
    | high24hr | string | 24小时最高价 |
    | low24hr | string | 24小时最低价 |
    



2. 获取某个交易对实时行情
    - 请求方式：GET
    - url：`https://{host}/quote/realTime`
    - 传入值：coins
    - 示例：https://www.dfex.com/polarisex/quote/realTime?coins=usdt_btc
    - 返回值data信息：
    
    | 字段名 | 数据类型 | 说明 |
    | --- | --- | --- |
    | buy | decimal | 买一价 |
    | high | decimal | 最高价 |
    | last | decimal | 最新成交价 |
    | low | decimal | 最低价 |
    | sell | decimal | 卖一价 |
    | vol | decimal | 成交量 |
    | currencyId | int | 交易币id |
    | baseCurrencyId | int | 基础币id |



3. 获取某个交易对最新深度
    - 请求方式：GET
    - url：`https://{host}/quote/tradeDeepin`
    - 示例：https://www.dfex.com/polarisex/quote/tradeDeepin?coins=usdt_btc
    - 传入值：
    
        | 字段名 | 数据类型 | 说明 |示例|
        | --- | --- | --- | --- |
        | coins | String | 基础币英文名_交易币英文名 |usdt_btc|
        | limit | int | 每次拉取多少条深度 |20|
        
    - 返回值data信息：
    
        | 字段名 | 数据类型 | 说明 |
        | --- | --- | --- |
        | asks | array | 卖队列，具体内容看下一个表格 |
        | bids | array | 买队列 |
        | last | decimal | 最新成交价 |
        | low | decimal | 最低价 |
        | sell | decimal | 卖一价 |
        | vol | decimal | 成交量 |
        | currencyId | int | 交易币id |
        | baseCurrencyId | int | 基础币id |




说明
数组对象第一个元素	价格
第二个元素	数量
- 示例：
```json
{
    "attachment": {
    "asks": [
    [
    "0.00937235",
    "0.4200"
    ]
    ],
    "bids": [
    [
    "0.00935215",
    "0.4900"
    ]
    ]
    },
    "message": "",
    "status": 200
}
```
4. 获取某个交易对成交列表

 - 请求方式：GET
    - url：`https://{host}/quote/tradeHistory`
    - 示例：https://www.dfex.com/polarisex/quote/tradeHistory?coins=usdt_btc&limit=5
    - 传入值：
    
        | 字段名 | 数据类型 | 说明 |示例|
        | --- | --- | --- | --- |
        | coins | String | 基础币英文名_交易币英文名 |usdt_btc|
        | limit | int | 每次拉取多少条深度 |20|
        
    - 返回值data信息：
    
        | 字段名 | 数据类型 | 说明 |
        | --- | --- | --- |
        | ﻿amount | decimal | 成交金额 |
        | ﻿number | decimal | 成交数量 |
        | ﻿price | decimal | 成交价 |
        | ﻿type | number | 买卖方向 |
        | ﻿date | number | ﻿成交时间 |









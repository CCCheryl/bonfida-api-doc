---
title: Bonfida API

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://bonfida.com'>Bonfida</a>
  - <a href='https://bonfida.com/dex'>Bonfida DEX</a>
  - <a href='https://bonfida.com/wallet'>Bonfida Wallet</a>

search: true

code_clipboard: true
---

# 介绍

欢迎使用Bonfida API！您可以通过我们的API来访问Serum Dex的数据库以及其它加密市场的分析。


目前的API访问频率限制是每秒30个请求 - 如果您搭建的项目需要更高的限制，请与我们联系。

# Serum项目

更多关于Serum的信息请访问[Serum项目](https://projectserum.com)

REST 接口 URL: `https://serum-api.bonfida.com`

## 获取所有交易对

```shell
curl "https://serum-api.bonfida.com/pairs"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    "ALEPH/USDT",
    "ALEPH/WUSDC",
    "BTC/USDT",
    "BTC/WUSDC",
    "ETH/USDT",
    "ETH/WUSDC",
    "SOL/USDT",
    "SOL/WUSDC"
  ]
}
```

提供Serum DEX上所有交易对列表。

### HTTP请求

`GET https://serum-api.bonfida.com/pairs`

## 获取最新成交信息（按交易对查询）

```shell
curl "https://serum-api.bonfida.com/trades/ETHUSDT"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "market": "ETH/USDT",
      "price": 451.51,
      "size": 0.5,
      "side": "buy",
      "time": 1604767562476.2188,
      "orderId": "833220983065386731245551",
      "feeCost": 0.225755,
      "marketAddress": "5abZGhrELnUnfM9ZUnvK6XJPoBU5eShZwfFPkdhAC7o"
    }
  ]
}
```

提供过去24小时中Serum DEX上所有的市场信息。

### HTTP请求

`GET https://serum-api.bonfida.com/trades/{marketName}`

### URL参数

|     参数   | 描述                                         |
| ---------- | ----------------------------------------------------- |
| marketName | 您想要进行数据检索的市场名称                     |

## 根据市场地址获取最新的交易信息

```shell
curl "https://serum-api.bonfida.com/trades/address/5abZGhrELnUnfM9ZUnvK6XJPoBU5eShZwfFPkdhAC7o"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "market": "ETH/USDT",
      "price": 451.51,
      "size": 0.5,
      "side": "buy",
      "time": 1604767562476.2188,
      "orderId": "833220983065386731245551",
      "feeCost": 0.225755,
      "marketAddress": "5abZGhrELnUnfM9ZUnvK6XJPoBU5eShZwfFPkdhAC7o"
    }
  ]
}
```

提供过去24小时中Serum DEX上所有的市场信息。

### HTTP请求

`GET https://serum-api.bonfida.com/trades/address/{marketAddress}`

### URL参数
|      参数     | 描述                                         |
| ------------- | ------------------------------------------------- |
| marketAddress | 您想要进行数据检索的市场地址                   |

## Get all recent trades

```shell
curl "https://serum-api.bonfida.com/trades"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "market": "ETH/USDT",
      "price": 451.51,
      "size": 0.5,
      "side": "buy",
      "time": 1604767562476.2188,
      "orderId": "833220983065386731245551",
      "feeCost": 0.225755,
      "marketAddress": "5abZGhrELnUnfM9ZUnvK6XJPoBU5eShZwfFPkdhAC7o"
    }
  ]
}
```

提供过去24小时中Serum DEX上所有的市场信息。

### HTTP请求

`GET https://serum-api.bonfida.com/trades`

## 获取交易量

```shell
curl "https://serum-api.bonfida.com/volumes/ETHUSDT"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "volumeUsd": 377446.7586900001,
      "volume": 835.2339999999999
    }
  ]
}
```

实时观察Serum DEX上24小时滚动交易量 - 使用‘所有’作为所有市场交易量合计的市场

### HTTP请求

`GET https://serum-api.bonfida.com/volumes/{marketName}`

### URL参数

| 参数       | 描述                                           |
| ---------- | ----------------------------------------------------- |
| marketName | 您想要进行数据检索的市场名称                       |

## 获取订单簿

```shell
curl "https://serum-api.bonfida.com/orderbooks/ETHUSDT"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": {
    "market": "ETH/USDT",
    "bids": [
      { "price": 452.77, "size": 5 },
      { "price": 452.71, "size": 0.5 },
      { "price": 452.17, "size": 10 },
      { "price": 451.98, "size": 184.238 },
      { "price": 451.64, "size": 221.099 },
      { "price": 450.6, "size": 200 },
      { "price": 449.94, "size": 228.41 },
      { "price": 449.9, "size": 232.205 },
      { "price": 449, "size": 295.667 },
      { "price": 448.66, "size": 412.566 },
      { "price": 446.04, "size": 468.99 },
      { "price": 446, "size": 644.819 },
      { "price": 443.78, "size": 536.219 },
      { "price": 436.98, "size": 700.985 },
      { "price": 399.19, "size": 0.15 }
    ],
    "asks": [
      { "price": 453.19, "size": 105.534 },
      { "price": 453.41, "size": 10 },
      { "price": 453.49, "size": 114.203 },
      { "price": 453.7, "size": 0.5 },
      { "price": 454.1, "size": 50 },
      { "price": 454.77, "size": 0.047 },
      { "price": 454.87, "size": 200 },
      { "price": 455.36, "size": 85.251 },
      { "price": 455.38, "size": 0.013 },
      { "price": 455.99, "size": 158.496 },
      { "price": 457.16, "size": 0.004 },
      { "price": 457.35, "size": 0.004 },
      { "price": 457.87, "size": 201.712 },
      { "price": 457.98, "size": 280.23 },
      { "price": 458.71, "size": 340.135 },
      { "price": 459.39, "size": 256.345 },
      { "price": 459.56, "size": 0.019 },
      { "price": 460.36, "size": 317.861 },
      { "price": 460.41, "size": 0.029 },
      { "price": 461.14, "size": 5 },
      { "price": 461.41, "size": 50 },
      { "price": 461.43, "size": 50 },
      { "price": 461.45, "size": 50 },
      { "price": 461.89, "size": 200 },
      { "price": 461.92, "size": 340.802 },
      { "price": 461.98, "size": 250 },
      { "price": 462.11, "size": 50 },
      { "price": 462.22, "size": 200 },
      { "price": 462.68, "size": 50 },
      { "price": 462.8, "size": 50 },
      { "price": 462.9, "size": 468.001 },
      { "price": 464.43, "size": 0.022 },
      { "price": 468.8, "size": 0.052 },
      { "price": 469.79, "size": 0.1 },
      { "price": 479.23, "size": 0.196 }
    ],
    "marketAddress": "5abZGhrELnUnfM9ZUnvK6XJPoBU5eShZwfFPkdhAC7o"
  }
}
```

提供过去24小时中Serum DEX上所有的市场信息。
 

### HTTP请求

`GET https://serum-api.bonfida.com/orderbooks/{marketName}`

### URL参数

| 参数  | 描述                                           |
| ---------- | ----------------------------------------------------- |
| marketName | 您想要进行数据检索的市场名称 |

## Get historical prices

```shell
curl "https://serum-api.bonfida.com/candles/BTCUSDC?resolution=3600"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "close": 16001.05,
      "open": 15942.05,
      "low": 15942.05,
      "high": 16013.3,
      "startTime": 1605416400000,
      "market": "BTC/USDC",
      "volumeBase": 0,
      "volumeQuote": 0
    },
    {
      "close": 15942.05,
      "open": 15949.95,
      "low": 15899.1,
      "high": 15978.5,
      "startTime": 1605412800000,
      "market": "BTC/USDC",
      "volumeBase": 0,
      "volumeQuote": 0
    }
  ]
}
```

### HTTP请求

`GET https://serum-api.bonfida.com/candles/{marketName}?resolution={resolution}&startTime={startTime}&endTime={endTime}&limit={limit}`

### URL参数

| 参数       | 描述                                               |
| ---------- | --------------------------------------------------------- |
| marketName | 您想要进行数据检索的市场名称     |
| resolution | 分辨率，每秒窗口长度。选项：60、3600、14400、86400 |
| startTime  | 开始时间，可选项（毫秒）                                          |
| endTime    | 结束时间，可选项（毫秒）                                          |
| limit      | 限制，可选项，最大值默认为1000。                           |

## 获取所有资金池

```shell
curl "https://serum-api.bonfida.com/pools"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "name": "USDT/SOL",
      "pool_identifier": "H2mJpdQTBcsfGUJvVJjRpPd95RKf2stDadJnR3Mf2qq7",
      "liquidity_locked": 190685.5960057655,
      "apy": 0.06389282452440433,
      "volume": 57038.58298187185,
      "mints": [
        "BQcdHdAQW1hczDbBi9hiegXAR7A98Q9jx3X3iBBBDiq4",
        "So11111111111111111111111111111111111111112"
      ],
      "liquidityA": 95928.930894,
      "liquidityAinUsd": 95928.930894,
      "liquidityB": 61912.228103081,
      "liquidityBinUsd": 94756.66511176547,
      "supply": 10.0216061,
      "fees": 171.11574894561554,
      "time": 1604204796661
    }
  ]
}
```

提供过去6小时Serum资金池的数据信息。每个资金池每隔三十分钟会增加一个新的数据点。

### HTTP请求

`GET https://serum-api.bonfida.com/pools`

以下接口返回最新的数据点:

`GET https://serum-api.bonfida.com/pools-recent`

## 获取资金池信息

```shell
curl "https://serum-api.bonfida.com/pools/BQcdHdAQW1hczDbBi9hiegXAR7A98Q9jx3X3iBBBDiq4/SRMuApVNdxXokk5GT7XD5cUUgXMBCoAz2LHeuAoKWRt?endTime=1605531090000&startTime=1605444690000&limit=100"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "name": "USDT/SRM",
      "pool_identifier": "2gJPRt8a9PNfjU4vFGtq4aH3ud1XY44tk9HvQVyF4eio",
      "liquidity_locked": 1522372.655400426,
      "apy": 1.1198276808045515,
      "volume": 2465262.921672771,
      "mints": [
        "BQcdHdAQW1hczDbBi9hiegXAR7A98Q9jx3X3iBBBDiq4",
        "SRMuApVNdxXokk5GT7XD5cUUgXMBCoAz2LHeuAoKWRt"
      ],
      "liquidityA": 760150.113927,
      "liquidityAinUsd": 760150.113927,
      "liquidityB": 588816.177268,
      "liquidityBinUsd": 762222.5414734259,
      "supply": 65.14360704,
      "fees": 7395.788765018314,
      "time": 1605529983607,
      "volume24hA": 124930.352732,
      "volume24hB": 98014.950623
    }
  ]
}
```

获取Serum资金池的历史数据。

### HTTP请求

`GET https://serum-api.bonfida.com/pools/{mintA}/{mintB}?startTime={startTime}&endTime={endTime}&limit={limit}`

### URL参数

| 参数      | 描述                    |
| --------- | ------------------------------ |
| mintA     | Mint address A 铸造地址A                |
| mintB     | Mint address B  铸造地址B               |
| startTime | 可选项（毫秒）             |
| endTime   | 可选项（毫秒）               |
| limit     | 可选项。最大默认值为1000 |

## 获取资金池交易信息

```shell
curl "https://serum-api.bonfida.com/pools/trades?symbolSource=BTC&symbolDestination=USDC&bothDirections=true"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "signature": "XaaGc8DKMza8uBfNMA5GzXATF1nz9cJMSnxPqRExzk4GG5ADhddsKi6mfeBAq3vd9G2GAUoAouEGnbgHrVw6Unb",
      "symbolSource": "BTC",
      "poolSourceMint": "9n4nbM75f5Ui33ZbPYXn59EwSgE8CGsHtAeTH5YFeJ9E",
      "symbolDestination": "USDC",
      "poolDestinationMint": "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v",
      "amountIn": 0.006892,
      "amountOut": 79.564554,
      "poolMintAuthority": "5W46iojjAEWk56oDUFL7FSyaqJEY7SvWvEZxBS38Daix",
      "time": 1604761992156
    }
  ]
}
```

提供过去24小时Serum Swap上所有交易信息列表

### HTTP请求

`GET https://serum-api.bonfida.com/pools/trades`

### URL参数

| 参数           | 描述                                        |
| ----------------- | -------------------------------------------------- |
| symbolSource      | `optional` 可选项，来源为Swap的通证                 |
| symbolDestination | `optional` 可选项，目标为Swap的通证            |
| bothDirections    | `optional` 可选项，双向进行交易检索     |

如果没有提供参数，将返回过去24小时中的所有交易

## 获取过去24小时资金池交易量 

```shell
curl "https://serum-api.bonfida.com/pools/volumes/recent"
```

> 上述指令得到的JSON格式的返回如下:

```json
{ "success": true, "data": [{ "volume": 408399.18767858105 }] }
```

实时观测Serum DEX上24小时滚动交易量

### HTTP请求

`GET https://serum-api.bonfida.com/pools/volumes/recent`

## 获取资金池历史交易量

```shell
curl "https://serum-api.bonfida.com/pools/volumes?mintA=9S4t2NEAiJVMvPdRYKVrfJpBafPBLtvbvyS3DecojQHw&mintB=EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v&endTime=1605605529000&startTime=1605259529000&limit=2"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "mintA": "9S4t2NEAiJVMvPdRYKVrfJpBafPBLtvbvyS3DecojQHw",
      "mintB": "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v",
      "volume": 9838.425721988495,
      "time": 1605571200000
    },
    {
      "mintA": "9S4t2NEAiJVMvPdRYKVrfJpBafPBLtvbvyS3DecojQHw",
      "mintB": "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v",
      "volume": 5999.188775463499,
      "time": 1605484800000
    },
    {
      "mintA": "9S4t2NEAiJVMvPdRYKVrfJpBafPBLtvbvyS3DecojQHw",
      "mintB": "EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v",
      "volume": 33847.21026596426,
      "time": 1605398400000
    }
  ]
}
```

提供资金池历史交易量数据。

### HTTP请求

`GET https://serum-api.bonfida.com/pools/volumes?mintA={mintA}&mintB={mintB}&endTime={endTime}&startTime={startTime}&limit={limit}`

### URL参数

| 参数      | 描述                   |
| --------- | ----------------------------- |
| mintA     | Mint address A  铸造地址A              |
| mintB     | Mint address B  铸造地址B              |
| startTime | 可选项（毫秒）              |
| endTime   | 可选项（毫秒）              |
| limit     | 可选项。最大默认值为100     |

## 获取资金池历史流动性

```shell
curl "https://serum-api.bonfida.com/pools/liquidity?mintA=9S4t2NEAiJVMvPdRYKVrfJpBafPBLtvbvyS3DecojQHw&mintB=EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v&endTime=1605605529000&startTime=1605259529000&limit=2"
```

> 上述指令得到的JSON格式的返回如下:

```json
{
  "success": true,
  "data": [
    {
      "mintA": "9n4nbM75f5Ui33ZbPYXn59EwSgE8CGsHtAeTH5YFeJ9E",
      "mintB": "SRMuApVNdxXokk5GT7XD5cUUgXMBCoAz2LHeuAoKWRt",
      "liquidityAinUsd": 624513.720168704,
      "liquidityBinUsd": 620145.0892474919,
      "liquidityA": 37.25022792401123,
      "liquidityB": 491481.99210968224,
      "time": 1605571200000
    }
  ]
}
```

提供资金池历史交易量数据。

### HTTP请求
`GET https://serum-api.bonfida.com/pools/liquidity?mintA={mintA}&mintB={mintB}&endTime={endTime}&startTime={startTime}&limit={limit}`

### URL参数

| 参数      | 描述                   |
| --------- | ----------------------------- |
| mintA     | Mint address A  铸造地址A              |
| mintB     | Mint address B  铸造地址B              |
| startTime | 可选项（毫秒）              |
| endTime   | 可选项（毫秒）              |
| limit     | 可选项。最大默认值为100       |   

## Trading View

Bonfida API接口的搭建是遵循了TradingView UDF（通用数据反馈）的规范。这意味着BonfidaAPI可以适用于任何TradingView的部件。您只需使用 `https://serum-api.bonfida.com/tv` 来获取TradingView里的部件构造函数 `datafeedUrl`文档.

```typescript
const defaultProps: ChartContainerProps = {
  // ...
  datafeedUrl: "https://serum-api.bonfida.com/tv"
  // ...
};

const widgetOptions: ChartingLibraryWidgetOptions = {
  // ...
  datafeed: new (window as any).Datafeeds.UDFCompatibleDatafeed(
    defaultProps.datafeedUrl
  )
  // ...
};

const tvWidget = new widget(widgetOptions);
```

# 交易所

REST endpoint URL: `https://bonfida.com/api`

## 获取下单延迟信息

```shell
curl "https://bonfida.com/api/latency-order"
```

> 上述指令得到的JSON格式的返回如下:

```json
[
  { "exchange": "bybit", "latency": 132578, "lastUpdate": 1604804743 },
  { "exchange": "ftx", "latency": 78446, "lastUpdate": 1604804743 },
  { "exchange": "binance", "latency": 29762, "lastUpdate": 1604804743 },
  { "exchange": "bitmex", "latency": 829601, "lastUpdate": 1604804743 }
]
```

通过Bybit、FTX、Binance、Bitmex的REST API下单接口的返回，监测出交易所最新延迟信息。延迟信息从`AWS Tokyo`进行监测。


以下接口从不同AWS地址进行监测:

- AWS 都柏林: `https://dublin.bonfida.com/api/latency-order`
- AWS 弗吉尼亚: `https://virginia.bonfida.com/api/latency-order`

### HTTP请求

`GET https://bonfida.com/api/latency-order`

## 获取未平仓合约信息

```shell
curl "https://bonfida.com/api/open-interest"
```

> 上述指令得到的JSON格式的返回如下:

```json
[
  {
    "exchange": "deribit",
    "openInterest": 183565810,
    "lastUpdate": 1604802624
  },
  {
    "exchange": "bybit",
    "openInterest": 557734465.52,
    "lastUpdate": 1604802624
  },
  { "exchange": "huobi", "openInterest": 207408300, "lastUpdate": 1604802624 },
  {
    "exchange": "binance",
    "openInterest": 591827555.328125,
    "lastUpdate": 1604802624
  },
  { "exchange": "okex", "openInterest": 142929500, "lastUpdate": 1604802624 },
  { "exchange": "bitmex", "openInterest": 357241514, "lastUpdate": 1604802624 },
  {
    "exchange": "ftx",
    "openInterest": 214813290.58319998,
    "lastUpdate": 1604802624
  }
]
```

返回Deribit、Bybit、Okex、FTX上的当前持仓量。

### HTTP请求

`GET https://bonfida.com/api/open-interest`

## 获取比特币的隐含波动率

```shell
curl "https://bonfida.com/api/vol/today"
```

> 上述指令得到的JSON格式的返回如下:

```json
0.6514701843261719
```

返回比特币隐含波动率。

### HTTP请求

`GET https://bonfida.com/api/vol/{time}`

### URL参数

| 参数      | 描述                                   |
| --------- | --------------------------------------------- |
| time      | `当日`, `次日`, `当周`, `次周` |

## 获取多空比

```shell
curl "https://bonfida.com/api/long-short-ratio?exchange=ftx&market=BTC-PERP"
```

> 上述指令得到的JSON格式的返回如下:

```json
{ "longRatio": 0.4852245862884161, "lastUpdate": 1604805231 }
```

返回指定交易所和指定市场的多空比。

### HTTP请求

`GET https://bonfida.com/api/long-short-ratio?exchange={exchange}&market={market}`

### URL参数

| 参数      | 描述                                                                                |
| --------- | ------------------------------------------------------------------------------------------ |
| exchange  | 您想要获取比率的交易所（仅支持FTX、Bybit、Binance、Phemex） |
| market    | 您想要获取比率的市场（例如： BTC-PERP）                                        |

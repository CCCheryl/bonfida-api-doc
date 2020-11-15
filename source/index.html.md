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

# Introduction

Welcome to the Bonfida API! You can use our API to access [Serum DEX](https://projectserum.com) data and other crypto market analytics.

The current rate limit is 30 requests per second - please reach out if you’re building something and need a higher limit.

# Project Serum

For more information about Serum visit [Project Serum](https://projectserum.com)

REST endpoint URL: `https://serum-api.bonfida.com`

## Get all pairs

```shell
curl "https://serum-api.bonfida.com/pairs"
```

> The above command returns JSON structured like this:

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

Provides a list of all trading pairs on the Serum DEX.

### HTTP Request

`GET https://serum-api.bonfida.com/pairs`

## Get recent trades by market name

```shell
curl "https://serum-api.bonfida.com/trades/ETHUSDT"
```

> The above command returns JSON structured like this:

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

Provides a list of all market fills from the last 24 hours on the Serum DEX.

### HTTP Request

`GET https://serum-api.bonfida.com/trades/{marketName}`

### URL Parameters

| Parameter  | Description                                           |
| ---------- | ----------------------------------------------------- |
| marketName | The name of the market you want to retrieve data from |

## Get recent trades by market address

```shell
curl "https://serum-api.bonfida.com/trades/address/5abZGhrELnUnfM9ZUnvK6XJPoBU5eShZwfFPkdhAC7o"
```

> The above command returns JSON structured like this:

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

Provides a list of all market fills from the last 24 hours on the Serum DEX.

### HTTP Request

`GET https://serum-api.bonfida.com/trades/address/{marketAddress}`

### URL Parameters

| Parameter     | Description                                       |
| ------------- | ------------------------------------------------- |
| marketAddress | The market address you want to retrieve data from |

## Get all recent trades

```shell
curl "https://serum-api.bonfida.com/trades"
```

> The above command returns JSON structured like this:

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

Provides a list of all market fills from the last 24 hours on the Serum DEX.

### HTTP Request

`GET https://serum-api.bonfida.com/trades`

## Get volume

```shell
curl "https://serum-api.bonfida.com/volumes/ETHUSDT"
```

> The above command returns JSON structured like this:

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

Provides a view of rolling 24 hour volume on the Serum DEX - use ‘all’ as the market for an aggregate of traded volume across all markets.

### HTTP Request

`GET https://serum-api.bonfida.com/volumes/{marketName}`

### URL Parameters

| Parameter  | Description                                           |
| ---------- | ----------------------------------------------------- |
| marketName | The name of the market you want to retrieve data from |

## Get orderbook

```shell
curl "https://serum-api.bonfida.com/orderbooks/ETHUSDT"
```

> The above command returns JSON structured like this:

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

Provides the current orderbook of the market.

### HTTP Request

`GET https://serum-api.bonfida.com/orderbooks/{marketName}`

### URL Parameters

| Parameter  | Description                                           |
| ---------- | ----------------------------------------------------- |
| marketName | The name of the market you want to retrieve data from |

## Get historical prices

```shell
curl "https://serum-api.bonfida.com/candles/BTCUSDC?resolution=3600"
```

> The above command returns JSON structured like this:

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

### HTTP Request

`GET https://serum-api.bonfida.com/candles/{marketName}?resolution={resolution}&startTime={startTime}&endTime={endTime}&limit={limit}`

### URL Parameters

| Parameter  | Description                                               |
| ---------- | --------------------------------------------------------- |
| marketName | The name of the market you want to retrieve data from     |
| resolution | Window length in seconds. options: 60, 3600, 14400, 86400 |
| startTime  | Optional (in ms)                                          |
| endTime    | Optional (in ms)                                          |
| limit      | Optional. Max 1000                                        |

## Get pools

```shell
curl "https://serum-api.bonfida.com/pools"
```

> The above command returns JSON structured like this:

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

Provides data about Serum pools over the last 24 hours. A new data point is added every 30 minutes for each pool.

### HTTP Request

`GET https://serum-api.bonfida.com/pools`

The following endpoint returns the most recent data points:

`GET https://serum-api.bonfida.com/pools-recent`

## Get pool trades

```shell
curl "https://serum-api.bonfida.com/pools/trades?symbolSource=BTC&symbolDestination=USDC&bothDirections=true"
```

> The above command returns JSON structured like this:

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

Provides a list of all trades fills from the last 24 hours on the Serum Swap

### HTTP Request

`GET https://serum-api.bonfida.com/pools/trades`

### URL Parameters

| Parameter         | Description                                        |
| ----------------- | -------------------------------------------------- |
| symbolSource      | `optional` Source coin of the swap                 |
| symbolDestination | `optional` Destination coin of the swap            |
| bothDirections    | `optional` To retrieve trades from both directions |

If no parameters are given it will return all trades from the last 24 hours

## Get pools volume

```shell
curl "https://serum-api.bonfida.com/pools/volumes/recent"
```

> The above command returns JSON structured like this:

```json
{ "success": true, "data": [{ "volume": 408399.18767858105 }] }
```

Provides a view of rolling 24 hour volume on the Serum Swap

### HTTP Request

`GET https://serum-api.bonfida.com/pools/volumes/recent`

# Exchanges

REST endpoint URL: `https://bonfida.com/api`

## Get order placement latencies

```shell
curl "https://bonfida.com/api/latency-order"
```

> The above command returns JSON structured like this:

```json
[
  { "exchange": "bybit", "latency": 132578, "lastUpdate": 1604804743 },
  { "exchange": "ftx", "latency": 78446, "lastUpdate": 1604804743 },
  { "exchange": "binance", "latency": 29762, "lastUpdate": 1604804743 },
  { "exchange": "bitmex", "latency": 829601, "lastUpdate": 1604804743 }
]
```

Returns the last latency measured for order placement through REST API for Bybit, FTX, Binance and Bitmex. The latency is measured from `AWS Tokyo`.

The following endpoints measure from different AWS locations:

- AWS Dublin: `https://dublin.bonfida.com/api/latency-order`
- AWS Virginia: `https://virginia.bonfida.com/api/latency-order`

### HTTP Request

`GET https://bonfida.com/api/latency-order`

## Get open interests

```shell
curl "https://bonfida.com/api/open-interest"
```

> The above command returns JSON structured like this:

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

Returns the open interest of Deribit, Bybit, Okex and FTX.

### HTTP Request

`GET https://bonfida.com/api/open-interest`

## Get BTC implied volatility

```shell
curl "https://bonfida.com/api/vol/today"
```

> The above command returns JSON structured like this:

```json
0.6514701843261719
```

Returns the BTC implied volatility.

### HTTP Request

`GET https://bonfida.com/api/vol/{time}`

### URL Parameters

| Parameter | Description                                   |
| --------- | --------------------------------------------- |
| time      | `today`, `tomorrow`, `this-week`, `next-week` |

## Get long and short ratios

```shell
curl "https://bonfida.com/api/long-short-ratio?exchange=ftx&market=BTC-PERP"
```

> The above command returns JSON structured like this:

```json
{ "longRatio": 0.4852245862884161, "lastUpdate": 1604805231 }
```

Returns long and short ratios for the specified exchange and specified market

### HTTP Request

`GET https://bonfida.com/api/long-short-ratio?exchange={exchange}&market={market}`

### URL Parameters

| Parameter | Description                                                                                |
| --------- | ------------------------------------------------------------------------------------------ |
| exchange  | Exchange from which you want the ratio (only FTX, Bybit, Binance and Phemex are supported) |
| market    | market from which you want the ratio (e.g BTC-PERP)                                        |

---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://bonfida.com'>Bonfida</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Bonfida API! You can use our API to access Serum DEX data and other crypto market analytics.

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

Provides a list of all market fills from the last 24 hours on the Serum DEX

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

Provides a list of all market fills from the last 24 hours on the Serum DEX

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

Provides a list of all market fills from the last 24 hours on the Serum DEX

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

Provides a list of all market fills from the last 24 hours on the Serum DEX

### HTTP Request

`GET https://serum-api.bonfida.com/volumes/{marketName}`

### URL Parameters

| Parameter  | Description                                                   |
| ---------- | ------------------------------------------------------------- |
| marketName | The name of the market address you want to retrieve data from |

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

Provides a list of all market fills from the last 24 hours on the Serum DEX

### HTTP Request

`GET https://serum-api.bonfida.com/orderbooks/{marketName}`

### URL Parameters

| Parameter  | Description                                                   |
| ---------- | ------------------------------------------------------------- |
| marketName | The name of the market address you want to retrieve data from |

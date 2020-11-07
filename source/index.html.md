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

`GET https://serum-api.bonfida.com/trades/{market}`

### URL Parameters

| Parameter | Description                               |
| --------- | ----------------------------------------- |
| market    | The market you want to retrieve data from |

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

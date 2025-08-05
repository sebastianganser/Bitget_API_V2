---
conversion_date: "2025-03-24"
document_title: "Candlestick Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/public/Candlesticks-Channel"
  - "https://www.bitget.com/api-doc/contract/market/Get-Candle-Data"
---

# Candlestick Channel

## Description

Retrieve the candlesticks data of a symbol. Data will be pushed every 500 ms.

The channel will push a snapshot after successful subscribed, later on the updates will be pushed.

If intended to query history data in a customized time range, please refer to [Get Candle Data](https://www.bitget.com/api-doc/contract/market/Get-Candle-Data).

## Request Parameters

| Parameter | Type    | Required | Description |
|-----------|---------|----------|-------------|
| op        | String  | Yes      | Operation, `subscribe` `unsubscribe` |
| args      | List<Object> | Yes | List of channels to request subscription |
| &emsp;> instType | String | Yes | Product type |
| &emsp;> channel | String | Yes | Channel name: `candle1m` (1 minute) `candle5m` (5 minutes) `candle15m` (15 minutes) `candle30m` (30 minutes) `candle1H` (1 hour) `candle4H` (4 hours) `candle12H` (12 hours) `candle1D` (1 day) `candle1W` (1 week) `candle6H` (6 hours) `candle3D` (3 days) `candle1M` (1-month line) `candle6Hutc` (6-hour line, UTC) `candle12Hutc` (12-hour line, UTC) `candle1Dutc` (1-day line, UTC) `candle3Dutc` (3-day line, UTC) `candle1Wutc` (weekly line, UTC) `candle1Mutc` (monthly line, UTC) |
| &emsp;> instId | String | Yes | Product ID, e.g. `ETHUSDT` |

## Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "candle1m",
            "instId": "BTCUSDT"
        }
    ]
}
```

## Response Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| event     | String | Event |
| arg       | Object | Subscribed channels |
| &emsp;> channel | String | Channel name, e.g., `candle1m`, `candle5m`, `candle15m`, etc. |
| &emsp;> instType | String | Product type |
| &emsp;> instId | String | Product ID, e.g., `ETHUSDT` |
| code      | String | Error code, returned only on error |
| msg       | String | Error message |

## Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "candle1m",
        "instId": "BTCUSDT"
    }
}
```

## Push Parameters

| Parameter | Type         | Description |
|-----------|--------------|-------------|
| arg       | Object       | Channels with successful subscription |
| &emsp;> channel | String | Channel name |
| &emsp;> instId  | String | Product ID |
| &emsp;> instType| String | Product type |
| data      | List<String> | Subscription data |
| &emsp;> index[0] | String | Start time, milliseconds format of Unix timestamp, e.g. `1597026383085` |
| &emsp;> index[1] | String | Opening price |
| &emsp;> index[2] | String | Highest price |
| &emsp;> index[3] | String | Lowest price |
| &emsp;> index[4] | String | Closing price |
| &emsp;> index[5] | String | Trading volume of left coin |
| &emsp;> index[6] | String | Trading volume of quote currency |
| &emsp;> index[7] | String | Trading volume of USDT |

## Push Data

```json
{
    "action": "snapshot",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "candle1m",
        "instId": "BTCUSDT"
    },
    "data": [
        [
            "1695685500000",
            "27000",
            "27000.5",
            "27000",
            "27000.5",
            "0.057",
            "1539.0155",
            "1539.0155"
        ]
    ],
    "ts": 1695715462250
}
```

---
conversion_date: "2025-03-27"
document_title: "History Position Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/private/History-Positions-Channel"
  - "https://www.bitget.com/api-doc/common/release-note"
---

# History Position Channel

## Description

Subscribe the position channel.

Data will be pushed when the position is totally closed.

## Request Parameters

| Parameter | Type         | Required | Description |
|----------|--------------|----------|-------------|
| op       | String        | Yes      | subscribe / unsubscribe |
| args     | List<Object>  | Yes      | List of channels to request subscription |
| > channel | String       | Yes      | Channel name: `positions-history` |
| > instType | String      | Yes      | Product type:<br>- `USDT-FUTURES`: USDT professional futures<br>- `COIN-FUTURES`: Mixed futures<br>- `USDC-FUTURES`: USDC professional futures<br>- `SUSDT-FUTURES`: USDT professional futures demo<br>- `SCOIN-FUTURES`: Mixed futures demo<br>- `SUSDC-FUTURES`: USDC professional futures demo |
| > instId | String        | Yes      | Symbol name, `default` represents all the symbols. Only `default` is supported now. |

### Request Example

```json
{
    "args":[
        {
            "channel":"positions-history",
            "instId":"default",
            "instType":"USDT-FUTURES"
        }
    ],
    "op":"subscribe"
}
```

## Response Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| event     | String | Event |
| arg       | Object | Subscribed channels |
| > channel | String | Channel name: `positions-history` |
| > instType | String | Product type:<br>- `USDT-FUTURES`<br>- `COIN-FUTURES`<br>- `USDC-FUTURES`<br>- `SUSDT-FUTURES`<br>- `SCOIN-FUTURES`<br>- `SUSDC-FUTURES` |
| > instId | String | `default` |
| code     | String | Error code |
| msg      | String | Error message |

### Response Example

```json
{
    "event":"subscribe",
    "arg":{
        "instType":"USDT-FUTURES",
        "channel":"positions-history",
        "instId":"default"
    }
}
```

## Push Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| action    | String | `'snapshot'` |
| arg       | Object | Channels with successful subscription |
| > channel | String | Channel name: `positions-history` |
| > instType | String | Product type:<br>- `USDT-FUTURES`<br>- `COIN-FUTURES`<br>- `USDC-FUTURES`<br>- `SUSDT-FUTURES`<br>- `SCOIN-FUTURES`<br>- `SUSDC-FUTURES` |
| > instId | String | `default` |
| data     | List<Object> | Subscription data |
| > posId  | String | Position ID |
| > instId | String | Product ID<br>[Delivery contract reference](https://www.bitget.com/api-doc/common/release-note) |
| > marginCoin | String | Currency of occupied margin |
| > marginMode | String | Margin mode:<br>- `fixed`: isolated mode<br>- `crossed`: crossed mode |
| > holdSide | String | Position direction |
| > posMode | String | Position mode |
| > openPriceAvg | String | Average entry price |
| > closePriceAvg | String | Average close price |
| > openSize | String | Open size |
| > closeSize | String | Close size |
| > achievedProfits | String | Realized PnL |
| > settleFee | String | Settle fee |
| > openFee | String | Total open fee |
| > closeFee | String | Total close fee |
| > cTime | String | Position creation time (Unix timestamp in ms), e.g. `1597026383085` |
| > uTime | String | Latest position update time (Unix timestamp in ms), e.g. `1597026383085` |

### Push Data

```json
{
    "action":"snapshot",
    "arg":{
        "instType":"USDT-FUTURES",
        "channel":"positions-history",
        "instId":"default"
    },
    "data":[
        {
            "posId":"1",
            "instId":"BTCUSDT",
            "marginCoin":"USDT",
            "marginMode":"crossed",
            "holdSide":"short",
            "posMode":"one_way_mode",
            "openPriceAvg":"20000.0",
            "closePriceAvg":"26221.0",
            "openSize":"0.010",
            "closeSize":"0.010",
            "achievedProfits":"-62.21000000",
            "settleFee":"-0.02277989",
            "openFee":"-0.12000000",
            "closeFee":"-0.15732600",
            "cTime":"1696907951177",
            "uTime":"1697090609976"
        }
    ],
    "ts":1697099840122
}
```


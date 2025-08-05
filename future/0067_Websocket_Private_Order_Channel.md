---
conversion_date: "2025-03-27"
document_title: "Order Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/private/Order-Channel"
  - "https://www.bitget.com/api-doc/common/release-note"
---

# Order Channel

## Description

Subscribe the order channel

Data will be pushed when the following events occurred:

- Open/Close orders are created  
- Open/Close orders are filled  
- Orders canceled  

---

## Request Parameters

| Parameter | Type | Required | Description |
|----------|------|----------|-------------|
| op       | String | Yes     | Operation, `subscribe` or `unsubscribe` |
| args     | List<Object> | Yes | List of channels to request subscription |
| ├─ channel | String | Yes | Channel name: `orders` |
| ├─ instType | String | Yes | Product type:<br>USDT-FUTURES – USDT professional futures<br>COIN-FUTURES – Mixed futures<br>USDC-FUTURES – USDC professional futures<br>SUSDT-FUTURES – USDT professional futures demo<br>SCOIN-FUTURES – Mixed futures demo<br>SUSDC-FUTURES – USDC professional futures demo |
| └─ instId | String | No | Trading pair, e.g. BTCUSDT<br>default: All trading pairs<br>For settled Futures, it only supports `default` |

---

## Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "orders",
            "instId": "default"
        }
    ]
}
```

---

## Response Parameters

| Parameter | Type | Description |
|----------|------|-------------|
| event    | String | Event |
| arg      | Object | Subscribed channels |
| ├─ channel | String | Channel name: `orders` |
| ├─ instType | String | Product type (same as above) |
| └─ instId | String | Product ID |
| code     | String | Error code |
| msg      | String | Error message |

---

## Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "orders",
        "instId": "default"
    }
}
```

---

## Push Parameters

| Parameter | Type | Description |
|----------|------|-------------|
| arg      | Object | Channels with successful subscription |
| ├─ channel | String | Channel name: `orders` |
| ├─ instType | String | Product type (same as above) |
| └─ instId | String | Product ID |
| data     | List<Object> | Subscription data |

---

## Push Data

```json
{
    "action": "snapshot",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "orders",
        "instId": "default"
    },
    "data": [
        {
            "accBaseVolume": "0.01",
            "cTime": "1695718781129",
            "clientOId": "1",
            "feeDetail": [
                {
                    "feeCoin": "USDT",
                    "fee": "-0.162003"
                }
            ],
            "fillFee": "-0.162003",
            "fillFeeCoin": "USDT",
            "fillNotionalUsd": "270.005",
            "fillPrice": "27000.5",
            "baseVolume": "0.01",
            "fillTime": "1695718781146",
            "force": "gtc",
            "instId": "BTCUSDT",
            "leverage": "20",
            "marginCoin": "USDT",
            "marginMode": "crossed",
            "notionalUsd": "270",
            "orderId": "1",
            "orderType": "market",
            "pnl": "0",
            "posMode": "hedge_mode",
            "posSide": "long",
            "price": "0",
            "priceAvg": "27000.5",
            "reduceOnly": "no",
            "stpMode": "cancel_taker",
            "side": "buy",
            "size": "0.01",
            "enterPointSource": "WEB",
            "status": "filled",
            "tradeScope": "T",
            "tradeId": "1111111111",
            "tradeSide": "open",
            "presetStopSurplusPrice": "21.4",
            "totalProfits": "11221.45",
            "presetStopLossPrice": "21.5",
            "uTime": "1695718781146"
        }
    ],
    "ts": 1695718781206
}
```


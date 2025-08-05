---
conversion_date: "2025-03-27"
document_title: "Position Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/private/Positions-Channel"
  - "https://www.bitget.com/api-doc/common/release-note"
---

# Position Channel | Bitget API

## Position Channel

### Description

Subscribe the position channel

Data will be pushed when the following events occurred:

- Open/Close orders are created  
- Open/Close orders are filled  
- Orders are canceled  

---

### Request Parameters

| Parameter | Type        | Required | Description |
|-----------|-------------|----------|-------------|
| op        | String      | Yes      | Operation, `subscribe` `unsubscribe` |
| args      | List<Object>| Yes      | List of channels to request subscription |
| &nbsp;&nbsp;&gt; channel | String | Yes | Channel name: `positions` |
| &nbsp;&nbsp;&gt; instType | String | Yes | Product type:<br>- `USDT-FUTURES` USDT professional futures<br>- `COIN-FUTURES` Mixed futures<br>- `USDC-FUTURES` USDC professional futures<br>- `SUSDT-FUTURES` USDT professional futures demo<br>- `SCOIN-FUTURES` Mixed futures demo<br>- `SUSDC-FUTURES` USDC professional futures demo |
| &nbsp;&nbsp;&gt; instId   | String | Yes | Symbol name, `default` represents all the symbols, Only `default` is supported now |

---

### Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "positions",
            "instId": "default"
        }
    ]
}
```

---

### Response Parameters

| Parameter | Type | Description |
|----------|------|-------------|
| event    | String | Event |
| arg      | Object | Subscribed channels |
| &nbsp;&nbsp;&gt; channel | String | Channel name: `positions` |
| &nbsp;&nbsp;&gt; instType | String | Product type:<br>- `USDT-FUTURES`<br>- `COIN-FUTURES`<br>- `USDC-FUTURES`<br>- `SUSDT-FUTURES`<br>- `SCOIN-FUTURES`<br>- `SUSDC-FUTURES` |
| &nbsp;&nbsp;&gt; instId | String | `default` |
| code     | String | Error code |
| msg      | String | Error message |

---

### Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "positions",
        "instId": "default"
    }
}
```

---

### Push Parameters

| Parameter | Type | Description |
|----------|------|-------------|
| action   | String | `'snapshot'` |
| arg      | Object | Channels with successful subscription |
| &nbsp;&nbsp;&gt; channel | String | Channel name: `positions` |
| &nbsp;&nbsp;&gt; instType | String | Product type:<br>- `USDT-FUTURES`<br>- `COIN-FUTURES`<br>- `USDC-FUTURES`<br>- `SUSDT-FUTURES`<br>- `SCOIN-FUTURES`<br>- `SUSDC-FUTURES` |
| &nbsp;&nbsp;&gt; instId | String | `default` |
| data     | List<Object> | Subscription data |
| &nbsp;&nbsp;&gt; posId | String | Position ID |
| &nbsp;&nbsp;&gt; instId | String | Product ID, delivery contract reference: [Bitget Release Notes](https://www.bitget.com/api-doc/common/release-note) |
| &nbsp;&nbsp;&gt; marginCoin | String | Currency of occupied margin |
| &nbsp;&nbsp;&gt; marginSize | String | Occupied margin (amount) |
| &nbsp;&nbsp;&gt; marginMode | String | Margin mode |
| &nbsp;&nbsp;&gt; holdSide | String | Position direction |
| &nbsp;&nbsp;&gt; posMode | String | Position mode |
| &nbsp;&nbsp;&gt; total | String | Open position size |
| &nbsp;&nbsp;&gt; available | String | Size of positions that can be closed |
| &nbsp;&nbsp;&gt; frozen | String | Amount of frozen margin |
| &nbsp;&nbsp;&gt; openPriceAvg | String | Average entry price |
| &nbsp;&nbsp;&gt; leverage | String | Leverage |
| &nbsp;&nbsp;&gt; achievedProfits | String | Realized PnL |
| &nbsp;&nbsp;&gt; unrealizedPL | String | Unrealized PnL |
| &nbsp;&nbsp;&gt; unrealizedPLR | String | Unrealized ROI |
| &nbsp;&nbsp;&gt; liquidationPrice | String | Estimated liquidation price |
| &nbsp;&nbsp;&gt; keepMarginRate | String | Maintenance margin rate |
| &nbsp;&nbsp;&gt; isolatedMarginRate | String | Actual margin ratio under isolated margin mode |
| &nbsp;&nbsp;&gt; marginRate | String | Occupancy rate of margin |
| &nbsp;&nbsp;&gt; breakEvenPrice | String | Position breakeven price |
| &nbsp;&nbsp;&gt; totalFee | String | Funding fee, the accumulated value of funding fee during the position. The initial value is empty, indicating that no funding fee has been charged yet. |
| &nbsp;&nbsp;&gt; deductedFee | String | Deducted transaction fees: transaction fees deducted during the position |
| &nbsp;&nbsp;&gt; cTime | String | Position creation time, milliseconds format of Unix timestamp, e.g. `1597026383085` |
| &nbsp;&nbsp;&gt; uTime | String | Latest position update time, milliseconds format of Unix timestamp, e.g. `1597026383085` |

---

### Push Data

```json
{
    "action": "snapshot",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "positions",
        "instId": "default"
    },
    "data": [
        {
            "posId": "1",
            "instId": "ETHUSDT",
            "marginCoin": "USDT",
            "marginSize": "9.5",
            "marginMode": "crossed",
            "holdSide": "short",
            "posMode": "hedge_mode",
            "total": "0.1",
            "available": "0.1",
            "frozen": "0",
            "openPriceAvg": "1900",
            "leverage": 20,
            "achievedProfits": "0",
            "unrealizedPL": "0",
            "unrealizedPLR": "0",
            "liquidationPrice": "5788.108475905242",
            "keepMarginRate": "0.005",
            "marginRate": "0.004416374196",
            "cTime": "1695649246169",
            "breakEvenPrice": "24778.97",
            "totalFee": "1.45",
            "deductedFee": "0.388",
            "uTime": "1695711602568",
            "autoMargin": "off"
        }
    ],
    "ts": 1695717430441
}
```


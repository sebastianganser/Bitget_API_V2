---
conversion_date: "2025-03-27"
document_title: "Trigger Order Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/private/Plan-Order-Channel"
  - "https://www.bitget.com/api-doc/common/release-note"
---

# Trigger Order Channel

## Description

Subscribe trigger order channel.

Data will be pushed when the trigger plans are opened, cancelled, modified, or triggered.

---

## Request Parameters

| Parameter | Type         | Required | Description                    |
|-----------|--------------|----------|--------------------------------|
| op        | String       | Yes      | Operation, `subscribe` `unsubscribe` |
| args      | List<Object> | Yes      | List of channels to request subscription |
| > channel | String       | Yes      | Channel name: `orders-algo`   |
| > instType| String       | Yes      | Product type:<br>- `USDT-FUTURES`: USDT professional futures<br>- `COIN-FUTURES`: Mixed futures<br>- `USDC-FUTURES`: USDC professional futures<br>- `SUSDT-FUTURES`: USDT professional futures demo<br>- `SCOIN-FUTURES`: Mixed futures demo<br>- `SUSDC-FUTURES`: USDC professional futures demo |
| > instId  | String       | No       | Trading pair                   |

### Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "orders-algo",
            "instId": "default"
        }
    ]
}
```

---

## Response Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| event     | String | Event       |
| arg       | Object | Subscribed channels |
| > channel | String | Channel name: `orders-algo` |
| > instType| String | Product type (see instType values above) |
| > instId  | String | Product ID  |
| code      | String | Error code  |
| msg       | String | Error message |

### Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "orders-algo",
        "instId": "default"
    }
}
```

---

## Push Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| action    | String | Push action |
| arg       | Object | Channels with successful subscription |
| > channel | String | Channel name: `orders-algo` |
| > instType| String | Product type (see instType values above) |
| > instId  | String | Product ID<br>Delivery contract reference: [Release Note](https://www.bitget.com/api-doc/common/release-note) |
| data      | List<Object> | Subscription data |

### Push Data Example

```json
{
    "action": "snapshot",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "orders-algo",
        "instId": "default"
    },
    "data": [
        {
            "instId": "BTCUSDT",
            "orderId": "1",
            "clientOid": "1",
            "triggerPrice": "27000.000000000",
            "triggerType": "fill_price",
            "triggerTime": "1695719197612",
            "planType": "pl",
            "price": "27000.000000000",
            "executePrice": "27000.000000000",
            "size": "0.020000000",
            "actualSize": "0.000000000",
            "orderType": "market",
            "side": "buy",
            "tradeSide": "open",
            "posSide": "long",
            "marginCoin": "USDT",
            "status": "live",
            "posMode": "hedge_mode",
            "enterPointSource": "web",
            "stopSurplusTriggerType": "fill_price",
            "stopLossTriggerType": "fill_price",
            "stpMode": "cancel_taker",
            "cTime": "1695719197612",
            "uTime": "1695719197612"
        }
    ],
    "ts": 1695719197733
}
```

---

## Additional Push Data Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| actualSize | String | Actual number of orders in coin |
| orderType | String | Order type:<br>- `limit`: limit order<br>- `market` |
| side | String | Order direction |
| tradeSide | String | Trade side trading direction |
| posSide | String | Position direction |
| marginCoin | String | Margin coin |
| status | String | Order status:<br>- `live`: plan order created<br>- `executed`: executed<br>- `fail_execute`: execute failed<br>- `cancelled`: cancelled<br>- `executing`: executing |
| posMode | String | Position mode:<br>- `one_way_mode`: one-way position mode<br>- `hedge_mode`: hedge position mode |
| enterPointSource | String | Order source:<br>- `WEB`: Orders created on the website<br>- `API`: Orders created on API<br>- `SYS`: System managed orders<br>- `ANDROID`: Orders created on Android app<br>- `IOS`: Orders created on iOS app |
| stopSurplusPrice | String | Execution price for take-profit:<br>Depends on `planType` - `pl`, `tp`, `ptp` |
| stopSurplusTriggerPrice | String | Trigger price for take-profit:<br>Depends on `planType` - `pl`, `tp`, `ptp`<br>Empty if none |
| stopSurplusTriggerType | String | Trigger type for take-profit:<br>Depends on `planType` - `pl`, `tp`, `ptp`<br>Empty if none |
| stopLossPrice | String | Execution price for stop-loss:<br>Depends on `planType` - `pl`, `sl`, `psl`<br>Empty if none |
| stopLossTriggerPrice | String | Trigger price for stop-loss:<br>Depends on `planType` - `pl`, `sl`, `psl` |
| stopLossTriggerType | String | Trigger type for stop-loss:<br>Depends on `planType` - `pl`, `sl`, `psl`<br>Empty if none |
| uTime | String | Order update time, in milliseconds (Unix timestamp) |
| stpMode | String | STP Mode:<br>- `none`: not setting STP<br>- `cancel_taker`<br>- `cancel_maker`<br>- `cancel_both` |


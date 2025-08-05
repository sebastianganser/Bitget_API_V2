---
conversion_date: "2025-03-27"
document_title: "Fill Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/private/Fill-Channel"
  - "https://www.bitget.com/api-doc/common/release-note#optimization-of-delivery-futures"
---

# Fill Channel

## Description

Trade details channel.

Data will be pushed when order filled.

---

## Request Parameters

| Parameter | Type         | Required | Description                                                                 |
|-----------|--------------|----------|-----------------------------------------------------------------------------|
| op        | String       | Yes      | Operation, `subscribe` or `unsubscribe`                                     |
| args      | List<Object> | Yes      | List of channels to request subscription                                    |
| > channel | String       | Yes      | Channel name: `fill`                                                        |
| > instType| String       | Yes      | Product type:<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| > instId  | String       | No       | Product ID or default, delivery contract reference: [Release Note](https://www.bitget.com/api-doc/common/release-note#optimization-of-delivery-futures) |

---

## Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "fill",
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
| > channel | String | Channel name: `fill` |
| > instType| String | Product type (same values as above) |
| > instId  | String | Product ID or default [Release Note](https://www.bitget.com/api-doc/common/release-note#optimization-of-delivery-futures) |
| code      | String | Error code  |
| msg       | String | Error message |

---

## Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "fill",
        "instId": "default"
    }
}
```

---

## 推送数据参数 (Push Data Parameters)

| 返回字段 (Field) | 参数类型 (Type) | 字段说明 (Description) |
|------------------|------------------|--------------------------|
| action           | String           | snapshot                 |
| arg              | Object           | Channels with successful subscription |
| > channel        | String           | Channel name: `fill`     |
| > instType       | String           | Product type (same as above) |
| > instId         | String           | Product ID or default [Release Note](https://www.bitget.com/api-doc/common/release-note#optimization-of-delivery-futures) |
| data             | List<Object>     | Subscription data        |

### Data Fields:

| Field         | Type     | Description |
|---------------|----------|-------------|
| orderId       | String   | Order ID    |
| tradeId       | String   | Trade ID    |
| symbol        | String   | Symbol Name |
| side          | String   | Trade direction:<br>`buy`: Buy<br>`sell`: Sell<br>In hedge position mode:<br>Open Long and Close Short → `buy`<br>Close Long and Open Short → `sell` |
| orderType     | String   | Order type: `limit`, `market` |
| posMode       | String   | Hold Mode: `one_way_mode`, `hedge_mode` |
| price         | String   | Order price |
| baseVolume    | String   | Amount of base coin |
| quoteVolume   | String   | Amount of denomination coin |
| profit        | String   | Realized PnL |
| tradeSide     | String   | Trade type:<br>`close`, `open`, `reduce_close_long`, `reduce_close_short`, `burst_close_long`, `burst_close_short`, `offset_close_long`, `offset_close_short`, `delivery_close_long`, `delivery_close_short`, `dte_sys_adl_close_long`, `dte_sys_adl_close_short`, `buy_single`, `sell_single`, `reduce_buy_single`, `reduce_sell_single`, `burst_buy_single`, `burst_sell_single`, `delivery_sell_single`, `delivery_buy_single`, `dte_sys_adl_buy_in_single_side_mode`, `dte_sys_adl_sell_in_single_side_mode` |
| tradeScope    | String   | Liquidity direction: `taker`, `maker` |
| feeDetail     | List<Object> | Transaction fee of the order |
| >> feeCoin    | String   | Currency of transaction fee |
| >> deduction  | String   | `yes` or `no` |
| >> totalDeductionFee | String | Fee of deduction |
| >> totalFee   | String   | Total fee |
| cTime         | String   | Create Time, milliseconds Unix timestamp |
| uTime         | String   | Update Time, milliseconds Unix timestamp |

---

## Push Data Example

```json
{
    "action":"snapshot",
    "arg":{
        "instType":"USDT-FUTURES",
        "channel":"fill",
        "instId":"default"
    },
    "data":[
        {
            "orderId":"111",
            "tradeId":"222",
            "symbol":"BTCUSDT",
            "side":"buy",
            "orderType":"market",
            "posMode":"one_way_mode",
            "price":"51000.5",
            "baseVolume":"0.01",
            "quoteVolume":"510.005",
            "profit":"0",
            "tradeSide":"open",
            "tradeScope":"taker",
            "feeDetail":[
                {
                    "feeCoin":"USDT",
                    "deduction":"no",
                    "totalDeductionFee":"0",
                    "totalFee":"-0.183717"
                }
            ],
            "cTime":"1703577336606",
            "uTime":"1703577336606"
        }
    ],
    "ts":1703577336700
}
```
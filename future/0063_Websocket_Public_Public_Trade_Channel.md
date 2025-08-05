---
conversion_date: "2025-03-24"
document_title: "Public Trade Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/public/New-Trades-Channel"
---

# Public Trade Channel

## Description

Get the public trade data (taker orders)

---

## Request Parameters

| Parameter | Type         | Required | Description                |
|----------|--------------|----------|----------------------------|
| op       | String       | Yes      | Operation, subscribe unsubscribe |
| args     | List<Object> | Yes      | op list                    |

**> instType** `String` **(Yes)**  
Product type  
- `USDT-FUTURES`: USDT professional futures  
- `COIN-FUTURES`: Mixed futures  
- `USDC-FUTURES`: USDC professional futures  
- `SUSDT-FUTURES`: USDT professional futures demo  
- `SCOIN-FUTURES`: Mixed futures demo  
- `SUSDC-FUTURES`: USDC professional futures demo

**> channel** `String` **(Yes)**  
Channel, `trade`

**> instId** `String` **(Yes)**  
Product ID  
e.g: `ETHUSDT`

---

## Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "trade",
            "instId": "BTCUSDT"
        }
    ]
}
```

---

## Response Parameters

| Parameter | Type   | Description         |
|----------|--------|---------------------|
| event    | String | event               |
| arg      | Object | arg list            |

**> instType**  
Product type  
- `USDT-FUTURES`: USDT professional futures  
- `COIN-FUTURES`: Mixed futures  
- `USDC-FUTURES`: USDC professional futures  
- `SUSDT-FUTURES`: USDT professional futures demo  
- `SCOIN-FUTURES`: Mixed futures demo  
- `SUSDC-FUTURES`: USDC professional futures demo

**> channel**  
Channel, `trade`

**> instId**  
Symbol name  
e.g: `ETHUSDT`

| Parameter | Type   | Description     |
|----------|--------|-----------------|
| code     | String | Error code      |
| msg      | String | Error message   |

---

## Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "trade",
        "instId": "BTCUSDT"
    }
}
```

---

## Push Parameters

| Parameter | Type   | Description     |
|----------|--------|-----------------|
| action   | String | action          |
| arg      | Object | arg             |

**> instType**  
Product type  
- `USDT-FUTURES`: USDT professional futures  
- `COIN-FUTURES`: Mixed futures  
- `USDC-FUTURES`: USDC professional futures  
- `SUSDT-FUTURES`: USDT professional futures demo  
- `SCOIN-FUTURES`: Mixed futures demo  
- `SUSDC-FUTURES`: USDC professional futures demo

**> channel**  
Channel, `trade`

**> instId**  
Symbol: `ETHUSDT`

| Parameter | Type         | Description         |
|----------|--------------|---------------------|
| data     | List<Object> | Data                |

**> ts** `String`  
Fill time: `1597026383085`

**> price** `String`  
Filled price

**> size** `String`  
Filled amount

**> side** `String`  
Filled side, `sell`/`buy`

**> tradeId** `String`  
tradeId

---

## Push Data

```json
{
    "action": "snapshot",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "trade",
        "instId": "BTCUSDT"
    },
    "data": [
        {
            "ts": "1695716760565",
            "price": "27000.5",
            "size": "0.001",
            "side": "buy",
            "tradeId": "1111111111"
        },
        {
            "ts": "1695716759514",
            "price": "27000.0",
            "size": "0.001",
            "side": "sell",
            "tradeId": "1111111111"
        }
    ],
    "ts": 1695716761589
}
```

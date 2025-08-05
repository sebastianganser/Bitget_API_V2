
---
conversion_date: "2025-03-27"
document_title: "Account channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/private/Account-Channel"
---

# Account channel

## Description

### Subscribe account channel

Data will be pushed when the following events occurred:
- Transfer balance to Futures account
- Trading voucher deposit
- Open/close orders are filled

### Request Parameters

| Parameter | Type         | Required | Description                                         |
|-----------|--------------|----------|-----------------------------------------------------|
| op        | String       | Yes      | Operation, `subscribe` or `unsubscribe`            |
| args      | List<Object> | Yes      | List of channels to request subscription           |

Within `args`:
- **instType** `String` **(Yes)**  
  Product type:
  - `USDT-FUTURES`: USDT professional futures  
  - `COIN-FUTURES`: Mixed futures  
  - `USDC-FUTURES`: USDC professional futures  
  - `SUSDT-FUTURES`: USDT professional futures demo  
  - `SCOIN-FUTURES`: Mixed futures demo  
  - `SUSDC-FUTURES`: USDC professional futures demo

- **channel** `String` **(Yes)**: Channel name  
- **coin** `String` **(Yes)**: Coin name. `default` represents all the coins. Only `default` is supported now.

### Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "account",
            "coin": "default"
        }
    ]
}
```

## Response Parameters

| Parameter | Type   | Description          |
|-----------|--------|----------------------|
| event     | String | Yes - Operation      |
| arg       | Object | Subscribed channels  |

Within `arg`:
- **instType** `String`  
  Product type:
  - `USDT-FUTURES`: USDT professional futures  
  - `COIN-FUTURES`: Futures settled in cryptocurrencies  
  - `USDC-FUTURES`: USDC professional futures  
  - `SUSDT-FUTURES`: USDT professional futures demo trading  
  - `SCOIN-FUTURES`: Futures settled in cryptocurrencies demo trading  
  - `SUSDC-FUTURES`: USDC professional futures demo trading  

- **channel** `String`: Channel name  
- **coin** `String`: `default`  

| Parameter | Type   | Description     |
|-----------|--------|-----------------|
| code      | String | Error code      |
| msg       | String | Error message   |

### Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "account",
        "coin": "default"
    }
}
```

## Push Parameters

| Parameter | Type   | Description                        |
|-----------|--------|------------------------------------|
| action    | String | `snapshot`                         |
| arg       | Object | Channels to request subscription   |

Within `arg`:
- **instType** `String`  
  Product type:
  - `USDT-FUTURES`: USDT professional futures  
  - `COIN-FUTURES`: Futures settled in cryptocurrencies  
  - `USDC-FUTURES`: USDC professional futures  
  - `SUSDT-FUTURES`: USDT professional futures demo trading  
  - `SCOIN-FUTURES`: Futures settled in cryptocurrencies demo trading  
  - `SUSDC-FUTURES`: USDC professional futures demo trading  

- **channel** `String`: Channel name  
- **coin** `String`: `default`

| Parameter               | Type         | Description                                       |
|-------------------------|--------------|---------------------------------------------------|
| data                    | List<Object> | Subscription data                                 |
| > marginCoin            | String       | Margin coin                                       |
| > frozen                | String       | Locked quantity (margin coin)                    |
| > available             | String       | Currently available assets                        |
| > maxOpenPosAvailable   | String       | Maximum available balance to open positions       |
| > maxTransferOut        | String       | Maximum transferable amount                       |
| > equity                | String       | Account assets                                    |
| > usdtEquity            | String       | Account equity in USD                             |
| > crossedRiskRate       | String       | Risk ratio in cross margin mode                   |
| > unrealizedPL          | String       | Unrealized PnL                                    |

### Push Data Example

```json
{
    "action": "snapshot",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "account",
        "coin": "default"
    },
    "data": [
      {
        "marginCoin": "USDT",
        "frozen": "0.00000000",
        "available": "11.98545761",
        "maxOpenPosAvailable": "11.98545761",
        "maxTransferOut": "11.98545761",
        "equity": "11.98545761",
        "usdtEquity": "11.985457617660",
        "crossedRiskRate": "0",
        "unrealizedPL": "0.000000000000"
      }
    ],
    "ts": 1695717225146
}
```


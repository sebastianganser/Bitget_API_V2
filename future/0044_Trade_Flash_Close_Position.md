---
conversion_date: "2025-03-20"
document_title: "Flash Close Position | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Flash-Close-Position"
---

# Flash Close Position | Bitget API

## Flash Close Position
**Frequency limit:** 1 time/1s (User ID)

### Description
Close position at market price

### HTTP Request
```
POST /api/v2/mix/order/close-positions
```

### Request Parameters
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| symbol        | String | No       | Trading pair |
| holdSide      | String | Optional | Position direction<br>1. In one-way position mode (buy or sell): This field should be left blank. Will be ignored if filled in.<br>2. In hedge-mode position (open or close): All positions will be closed if the field is left blank; Positions of the specified direction will be closed if the field is filled in.<br>`long`: Long position;<br>`short`: Short position |
| productType   | String | Yes      | Product type:<br>- `USDT-FUTURES`: USDT professional futures<br>- `COIN-FUTURES`: Mixed futures<br>- `USDC-FUTURES`: USDC professional futures<br>- `SUSDT-FUTURES`: USDT professional futures demo<br>- `SCOIN-FUTURES`: Mixed futures demo<br>- `SUSDC-FUTURES`: USDC professional futures demo |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/close-positions" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json" \
  -d '{"symbol": "BTCUSDT","productType":"USDT-FUTURES","holdSide": "long"}'
```

### Response Parameters
| Parameter    | Type         | Description |
|--------------|--------------|-------------|
| successList  | List<Object> | The collection of successfully closed orders |
| > orderId    | String       | Order ID |
| > clientOid  | String       | Customize order ID |
| > symbol     | String       | The Symbol |
| failureList  | List<Object> | The collection of unsuccessfully closed orders<br>The close order may fail when the pair is in delivery or in risk control handling |
| > orderId    | String       | Order ID |
| > clientOid  | String       | Customize order ID |
| > symbol     | String       | The Symbol |
| > errorMsg   | String       | Failure reason |
| > errorCode  | String       | Failure code |

### Response Example
```json
{
  "code": "00000", 
  "data": {
    "successList": [
      {
        "orderId": "123", 
        "clientOid": "xxxxx",
        "symbol": "BTCUSDT"
      }
    ], 
    "failureList": [
      {
        "orderId": "1234", 
        "clientOid": "321", 
        "symbol": "BTCUSDT",
        "errorMsg": "xxx", 
        "errorCode": "xxxx"
      }
    ]
  }, 
  "msg": "success", 
  "requestTime": 1627293504612
}
```

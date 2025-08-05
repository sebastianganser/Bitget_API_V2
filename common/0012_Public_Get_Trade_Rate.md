---
conversion_date: "2025-03-11"
document_title: "Get Trade Rate | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/public/Get-Trade-Rate"
---

# Get Trade Rate | Bitget API

## Get Trade Rate

**Frequency limit:** 10 times/1s (UID)

### Description

Get Trade Rate

### HTTP Request

```
GET /api/v2/common/trade-rate
```

### Request Parameter

| Parameter     | Type   | Required | Description                                |
|---------------|--------|----------|--------------------------------------------|
| symbol        | String | Yes      | Trading pair name, e.g. BTCUSDT            |
| businessType  | String | Yes      | Business type                              |
|               |        |          | - mix contract                             |
|               |        |          | - spot Spot                                |
|               |        |          | - margin leverage                          |

### Request Example

```
curl "https://api.bitget.com/api/v2/common/trade-rate?symbol=BTC" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameter

| Parameter      | Type   | Description                                              |
|----------------|--------|----------------------------------------------------------|
| makerRate      | String | Pending Order Handling Rates - Fractional form (e.g., 0.0002 for two parts per million) |
| takerFeeRate   | String | Taking Order Handling Rates - Fractional form (e.g., 0.0002 for two parts per million)  |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1683875302853,
    "data": {
        "makerFeeRate": "0.0002",
        "takerFeeRate": "0.0006"
    }
}
```

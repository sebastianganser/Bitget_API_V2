---
conversion_date: "2025-03-12"
document_title: "Get Trade data support symbols | Bitget API"
extracted_urls:
  - "https://api.bitget.com/api-doc/common/apidata/Get-Big-Data-Symbol"
---

# Get Trade data support symbols | Bitget API

## Get Trade data support symbols

**Rate limit:** 1 req/1s (IP)

### Description

Get Trade data support symbols

### HTTP Request

```
GET /api/v2/spot/market/support-symbols
```

### Request Parameters

N/A

### Request Example

```
curl "https://api.bitget.com/api/v2/spot/market/support-symbols"
```

### Response Parameters

| Parameter    | Type | Description              |
|--------------|------|--------------------------|
| spotList     | List | Spot data symbols        |
| futureList   | List | Futures data symbols     |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": {
        "spotList": ["BTCUSDT","ETHUSDT"],
        "futureList": ["BTCUSDT","ETHUSDT"]
    }
}
```

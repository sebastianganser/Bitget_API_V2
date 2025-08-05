---
conversion_date: "2025-03-12"
document_title: "Bot account | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/account/Bot-Assets"
---

# Bot account | Bitget API

## Bot account  
**Frequency limit:** 10 times/1s (User ID)

### HTTP Request

```
GET /api/v2/account/bot-assets
```

### Request Parameters

| Parameter    | Type   | Required | Description        |
|--------------|--------|----------|--------------------|
| accountType  | String | No       | bot account type: `futures`, `spot` |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/account/bot-assets?accountType=futures" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*******" \
  -H "ACCESS-PASSPHRASE:*****" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:en-US" \
  -H "Content-Type: application/json"
```

### Response Parameters

| Parameter    | Type         | Description        |
|--------------|--------------|--------------------|
| data         | List<Object> | assetsList         |
| → coin       | String       | coin               |
| → available  | String       | available          |
| → equity     | String       | account assets     |
| → bonus      | String       | trading bonuses    |
| → frozen     | String       | in orders          |
| → usdtValue  | String       | USDT values        |

### Response Example

```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1712131247803,
  "data": [
    {
      "coin": "USDT",
      "available": "84.61136285",
      "equity": "140.94936285",
      "bonus": "0",
      "frozen": "0",
      "usdtValue": "140.949362850622"
    }
  ]
}
```

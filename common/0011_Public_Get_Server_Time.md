---
conversion_date: "2025-03-11"
document_title: "Get Server Time | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/public/Get-Server-Time"
---

# Get Server Time | Bitget API

## Get Server Time

**Frequency limit:** 20 times/1s (IP)

### Description
Getting server time, Unix millisecond timestamp

### HTTP Request
```
GET /api/v2/public/time
```

### Request Parameters
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| N/A       | -    | -        | -           |

### Request Example
```
curl "https://api.bitget.com/api/v2/public/time"
```

### Response Parameters
| Parameter   | Type   | Description                                |
|------------|--------|--------------------------------------------|
| serverTime | String | Server time, Unix millisecond timestamp, e.g. 1690196141868 |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1688008631614,
    "data": {
        "serverTime": "1688008631614"
    }
}
```

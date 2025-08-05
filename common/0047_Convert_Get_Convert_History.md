---
conversion_date: "2025-03-12"
document_title: "Get Convert History | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/convert/Get-Convert-Record"
---

# Get Convert History | Bitget API

## Get Convert History
**Frequency limit:** 10 times/1s (User ID)

### Description
Get Convert History

### HTTP Request
```
GET /api/v2/convert/convert-record
```

### Request Parameters
| Parameter     | Type   | Required | Description                                        |
|---------------|--------|----------|----------------------------------------------------|
| startTime     | String | Yes      | Start time, Unix millisecond timestamps            |
| endTime       | String | Yes      | End time, Unix millisecond timestamps              |
|               |        |          | The maximum interval between startTime and endTime is 90 days. |
| limit         | String | No       | Default 20 Maximum 100                             |
| idLessThan    | String | No       | ID of the last record endId                        |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/convert/convert-record?startTime=1686128558000&endTime=1686214958000&limit=10"    -H "ACCESS-KEY:*******"    -H "ACCESS-SIGN:*"    -H "ACCESS-PASSPHRASE:*"    -H "ACCESS-TIMESTAMP:1659076670000"    -H "locale:en-US"    -H "Content-Type: application/json"
```

### Response Parameters
| Parameter      | Type   | Description                                  |
|----------------|--------|----------------------------------------------|
| dataList       | List   | List                                          |
| id             | String | Splash Record id                              |
| ts             | String | Time of generation of flash transfer records |
| cnvtPrice      | String | Coin swap price                               |
| fee            | String | Transaction fee                               |
| fromCoinSize   | String | Coin swap amount                              |
| fromCoin       | String | Switch                                        |
| toCoinSize     | String | Get the number of target coins                |
| toCoin         | String | Target currency                               |
| endId          | String | Pagination                                    |

### Response Example
```json
{
    "code": "00000",
    "data": {
        "dataList": [
            {
                "id": "1",
                "ts": "1688527512229",
                "cnvtPrice": "0.00052268",
                "fee": "0",
                "fromCoinSize": 100,
                "fromCoin": "USDT",
                "toCoinSize": "0.23206967",
                "toCoin": "ETH"
            }
        ],
        "endId": "1"
    },
    "msg": "success",
    "requestTime": 1627293612502
}
```


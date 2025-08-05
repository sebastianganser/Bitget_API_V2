---
conversion_date: "2025-03-12"
document_title: "Get BGB Convert Coins | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/bgb-convert/Get-BGB-Convert-Coins"
---

# Get BGB Convert Coins

**Frequency limit:** 10 times/1s (User ID)

## Description
Get a list of Convert BGB Currencies

## HTTP Request
```
GET /api/v2/convert/bgb-convert-coin-list
```

## Request Parameters
N/A

## Request Example
```bash
curl "https://api.bitget.com/api/v2/convert/bgb-convert-coin-list" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

## Response Parameters
| Parameter       | Type   | Description                                |
|----------------|--------|--------------------------------------------|
| coin           | String | Token name                                 |
| available      | String | Currency accounts available                |
| bgbEstAmount   | String | Expected number of BGB redeemable          |
| precision      | String | BGB scale                                  |
| feeDetail      | String | Fee detail                                 |
| > feeRate      | String | Fee rate                                   |
| > fee          | String | Fee                                        |
| cTime          | String | Currently Time (timestamp in milliseconds) |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1703831563264,
    "data": {
        "coinList": [
            {
                "coin": "SEAM",
                "available": "0.00303329",
                "bgbEstAmount": "0.03794680",
                "precision": "8",
                "feeDetail": [
                    {
                        "feeRate": "0.02",
                        "fee": "0.00075893"
                    }
                ],
                "cTime": "1703831563514"
            }
        ]
    }
}
```


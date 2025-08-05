---
conversion_date: "2025-03-12"
document_title: "Get Convert Coins | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/convert/Get-Convert-Currencies"
---

# Get Convert Coins | Bitget API

**Frequency limit:** 10 times/1s (User ID)

## Description
Get a list of Flash Currencies

## HTTP Request
```
GET /api/v2/convert/currencies
```

## Request Parameters
N/A

## Request Example
```bash
curl "https://api.bitget.com/api/v2/convert/currencies" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

## Response Parameters
| Parameter   | Type   | Description |
|------------|--------|-------------|
| coin       | String | Token name |
| available  | String | Currency accounts available |
| maxAmount  | String | Maximum available quantity. As `fromCoin` means maximum consumable quantity, as `toCoin` means maximum redeemable quantity. |
| minAmount  | String | Minimum usable quantity. As `fromCoin` represents the minimum consumable quantity, as `toCoin` represents the minimum redeemable quantity. |

## Response Example
```json
{
    "code": "00000",
    "data": [
        {
            "coin": "ETH",
            "available": "0.9994",
            "maxAmount": "5",
            "minAmount": "0.0005"
        }
    ],
    "msg": "success",
    "requestTime": 1627293612502
}
```


---
conversion_date: "2025-03-18"
document_title: "My Estimated Open Count | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Est-Open-Count"
---

# My Estimated Open Count

**Frequency limit:** 10 times/1s (uid)

## Description
Get estimated open count per UID

## HTTP Request
`GET /api/v2/mix/account/open-count`

## Request Parameters
| Parameter     | Type   | Required | Description                             |
|--------------|--------|----------|-----------------------------------------|
| symbol       | String | Yes      | Trading pair, e.g., ETHUSDT              |
| productType  | String | Yes      | Product type:<br>USDT-FUTURES USDT professional futures<br>COIN-FUTURES Mixed futures<br>USDC-FUTURES USDC professional futures<br>SUSDT-FUTURES USDT professional futures demo<br>SCOIN-FUTURES Mixed futures demo<br>SUSDC-FUTURES USDC professional futures demo |
| marginCoin   | String | Yes      | Margin coin                              |
| openAmount   | String | Yes      | Margin amount                            |
| openPrice    | String | Yes      | Price of the order                       |
| leverage     | String | No       | Leverage (default: 20)                   |

## Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/account/open-count?productType=usdt-futures&symbol=ethusdt&marginCoin=USDT&openPrice=23189.5&leverage=20&openAmount=5000" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

## Response Parameters
| Parameter | Type   | Description             |
|----------|--------|-------------------------|
| size     | String | Estimated open size     |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1695812285073,
    "data": {
        "size": "0.47"
    }
}
```


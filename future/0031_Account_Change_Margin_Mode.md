---
conversion_date: "2025-03-19"
document_title: "Change Margin Mode | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Change-Margin-Mode"
---

# Change Margin Mode | Bitget API

## Change Margin Mode

**Frequency limit:** 5 times/1s (uid)

### Description
This interface cannot be used when the users have an open position or an order.

### HTTP Request
```
POST /api/v2/mix/account/set-margin-mode
```

### Request Parameters
| Parameter     | Type   | Required | Description                                                                 |
|--------------|--------|----------|-----------------------------------------------------------------------------|
| symbol       | String | Yes      | Trading pair. e.g. BTCUSDT                                                 |
| productType  | String | Yes      | Product type:<br>USDT-FUTURES: USDT professional futures<br>COIN-FUTURES: Mixed futures<br>USDC-FUTURES: USDC professional futures<br>SUSDT-FUTURES: USDT professional futures demo<br>SCOIN-FUTURES: Mixed futures demo<br>SUSDC-FUTURES: USDC professional futures demo |
| marginCoin   | String | Yes      | Margin coin, must be capitalized                                           |
| marginMode   | String | Yes      | Margin mode:<br>isolated: isolated margin mode<br>crossed: crossed margin mode |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/account/set-margin-mode" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"symbol": "btcusdt","productType": "USDT-FUTURES","marginCoin": "usdt","marginMode": "isolated"}'
```

### Response Parameters
| Parameter      | Type   | Description                      |
|---------------|--------|----------------------------------|
| symbol        | String | Trading pair name                |
| marginCoin    | String | Margin coin                      |
| longLeverage  | String | Leverage of long positions       |
| shortLeveage  | String | Leverage of short positions      |
| marginMode    | String | Margin mode:<br>isolated: isolated margin mode<br>crossed: crossed margin mode |

### Response Example
```json
{
    "code": "00000",
    "data": {
        "symbol": "BTCUSDT",
        "marginCoin": "USDT",
        "longLeverage": "25",
        "shortLeverage": "20",
        "marginMode": "isolated"
    },
    "msg": "success",
    "requestTime": 1627293445916
}
```


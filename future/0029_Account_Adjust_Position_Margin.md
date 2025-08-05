---
conversion_date: "2025-03-18"
document_title: "Adjust Position Margin | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Change-Margin"
---

# Adjust Position Margin | Bitget API

## Adjust Position Margin

**Rate limit:** 5 req/sec/UID

### Description
Add or reduce the margin (only for isolated margin mode)

### HTTP Request
```
POST /api/v2/mix/account/set-margin
```

### Request Parameters
| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| symbol        | String | Yes      | Trading pair |
| productType   | String | Yes      | Product type:<br>USDT-FUTURES – USDT professional futures<br>COIN-FUTURES – Mixed futures<br>USDC-FUTURES – USDC professional futures<br>SUSDT-FUTURES – USDT professional futures demo<br>SCOIN-FUTURES – Mixed futures demo<br>SUSDC-FUTURES – USDC professional futures demo |
| marginCoin    | String | Yes      | Margin coin must be capitalized |
| holdSide      | String | Yes      | Position direction:<br>long – long position<br>short – short position |
| amount        | String | Yes      | Margin amount, positive means increase, and negative means decrease |

### Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/mix/account/set-margin" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"symbol": "btcusdt","productType": "USDT-FUTURES","marginCoin": "usdt","amount": "20","holdSide": "long"}'
```

### Response Parameters
| Parameter     | Type   | Description |
|---------------|--------|-------------|
| code          | String | '00000': success; others: fail |

### Response Example
```json
{
    "code": "00000",
    "data": "",
    "msg": "success",
    "requestTime": 1627293357336
}
```


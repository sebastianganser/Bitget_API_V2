---
conversion_date: "2025-03-19"
document_title: "Change Position Mode | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/account/Change-Hold-Mode"
---

# Change Position Mode

**Frequency limit:** 5 times/1s (uid)

## Description

Adjust the position mode between 'one way mode' and 'hedge mode'.

If you want to change the user's position mode on all symbol contracts, you need to specify hedge mode positions or one-way positions.

> **Note:** The position mode can't be adjusted when there is an open position order under the product type. Changes the user's position mode for all symbol futures: hedging mode or one-way mode. When users hold positions or orders on any side of any trading pair in the specific product type, the request may fail.

## HTTP Request

```
POST /api/v2/mix/account/set-position-mode
```

## Request Parameters

| Parameter     | Type   | Required | Description                                                                 |
|--------------|--------|----------|-----------------------------------------------------------------------------|
| productType  | String | Yes      | Product type <br> USDT-FUTURES: USDT professional futures <br> COIN-FUTURES: Mixed futures <br> USDC-FUTURES: USDC professional futures <br> SUSDT-FUTURES: USDT professional futures demo <br> SCOIN-FUTURES: Mixed futures demo <br> SUSDC-FUTURES: USDC professional futures demo |
| posMode      | String | Yes      | Position mode <br> one_way_mode: one-way mode <br> hedge_mode: hedge mode |

## Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/account/set-position-mode" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
   -d '{"productType": "USDT-FUTURES","posMode": "one_way_mode"}'
```

## Response Parameters

| Parameter | Type   | Description                                                 |
|----------|--------|-------------------------------------------------------------|
| posMode  | String | Position mode <br> one_way_mode: one-way mode <br> hedge_mode: hedge mode |

## Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "data": {
        "posMode": "one_way_mode"
    },
    "requestTime": 1627293445916
}
```


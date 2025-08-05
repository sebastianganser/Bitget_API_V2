---
conversion_date: "2025-03-20"
document_title: "Trigger Sub Order | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/plan/Plan-Sub-Orders"
---

# Trigger Sub Order

**Rate limit:** 10 req/sec/UID

## Description
Get trigger executed futures orders

## HTTP Request
```
GET /api/v2/mix/order/plan-sub-order
```

## Request Parameters
| Parameter     | Type   | Required | Description                                                                 |
|--------------|--------|----------|-----------------------------------------------------------------------------|
| planType     | String | Yes      | Trigger order type<br>normal_plan: average trigger order<br>track_plan: trailing stop order |
| planOrderId  | String | Yes      | Trigger order ID                                                            |
| productType  | String | Yes      | Product type:<br>USDT-FUTURES – USDT professional futures<br>COIN-FUTURES – Mixed futures<br>USDC-FUTURES – USDC professional futures<br>SUSDT-FUTURES – USDT professional futures demo<br>SCOIN-FUTURES – Mixed futures demo<br>SUSDC-FUTURES – USDC professional futures demo |

## Request Example
```bash
curl "https://api.bitget.com/api/v2/mix/order/plan-sub-order?planOrderId=xxxxxxxxxxxxxxxxxx&productType=USDT-FUTURES&planType=normal_plan" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

## Response Parameters
| Parameter | Type   | Description                                                           |
|----------|--------|-----------------------------------------------------------------------|
| orderId  | String | Futures order ID                                                      |
| price    | String | Price of the futures order                                            |
| type     | String | Order type<br>limit<br>market                                         |
| status   | String | Plan order trigger status:<br>success: trigger success<br>fail: trigger failed<br>cancelled: cancelled<br>in_progress: trigger spot placing order<br>in_progress_tracking: tracking trigger |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1710813939206,
    "data": [
        {
            "orderId": "xxxxxxxxxxxxx",
            "price": "0.4188",
            "type": "limit",
            "status": "success"
        }
    ]
}
```

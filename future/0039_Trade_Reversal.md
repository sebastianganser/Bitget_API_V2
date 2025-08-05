---
conversion_date: "2025-03-20"
document_title: "Reversal | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/trade/Reversal"
---

# Reversal | Bitget API

**Rate limit:** 10 req/sec/UID  
**Rate limit (copy trading traders):** 1 req/sec/UID

## Description

**side** and **tradeSide**:

- In **one-way-mode**, do NOT add the `tradeSide` parameter in the request.
- In **hedge-mode**, `tradeSide` is required.
  - Reversal of the current long position and opening a short position: `side=buy`, `tradeSide`
  - Reversal of the current short position and opening a long position: `side=sell`, `tradeSide`

**size**: Represents the reversal size.

- In **one-way-mode**, the whole position will be reversed if no `size` was set in the request.
- In **hedge-mode**:
  - If the `size` set is less than the current position size, the size of the position will be closed and the same size reversal position will be opened.
    - Example: For an ETHUSDT size 20 long position, if the `size` is set to 3 in the request, the current long position size will be reduced to 17, and a new size 3 short position will be opened.
  - If the `size` set is equal to or more than the current position size, the whole position will be reversed.
    - Example: For an ETHUSDT size 10 long position, if the `size` is set to 10 or 11 in the request, then the current position will be closed and a new 10 size short position will be opened.

## HTTP Request

```
POST /api/v2/mix/order/click-backhand
```

## Request Parameters

| Parameter     | Type   | Required | Description |
|---------------|--------|----------|-------------|
| symbol        | String | Yes      | Trading pair, e.g., ETHUSDT |
| marginCoin    | String | Yes      | Margin coin, e.g., USDT |
| productType   | String | Yes      | Product type:<br>- USDT-FUTURES: USDT professional futures<br>- COIN-FUTURES: Mixed futures<br>- USDC-FUTURES: USDC professional futures<br>- SUSDT-FUTURES: USDT professional futures demo<br>- SCOIN-FUTURES: Mixed futures demo<br>- SUSDC-FUTURES: USDC professional futures demo |
| size          | String | Yes      | Amount |
| side          | String | No       | Order direction:<br>- buy: Buy<br>- sell: Sell |
| tradeSide     | String | No       | Direction (required in open and close in hedge mode; ignored in one-way positions):<br>Notes:<br>- Open long: `Buy`, `tradeSide=Open`<br>- Open short: `Sell`, `tradeSide=Open`<br>- Close long: `Buy`, `tradeSide=Close`<br>- Close short: `Sell`, `tradeSide=Close` |
| clientOid     | String | No       | Custom order ID |
| marginCoin    | String | Yes      | Margin coin |

## Request Example

```bash
curl -X POST "https://api.bitget.com/api/v2/mix/order/click-backhand" \
  -H "ACCESS-KEY:your apiKey" \
  -H "ACCESS-SIGN:*" \
  -H "ACCESS-PASSPHRASE:*" \
  -H "ACCESS-TIMESTAMP:1659076670000" \
  -H "locale:zh-CN" \
  -H "Content-Type: application/json" \
  -d '{
    "symbol": "ethusdt", 
    "productType": "USDT-FUTURES", 
    "marginCoin": "usdt", 
    "size": "30", 
    "clientOid": "12345"
}'
```

## Return Parameter

| Parameter  | Type   | Description         |
|-----------|--------|---------------------|
| orderId   | String | Order ID            |
| clientOid | String | Custom order ID     |

## Response Example

```json
{
  "code": "00000",
  "msg": "success",
  "requestTime": 1695806875837,
  "data": {
    "clientOid": "121211212122",
    "orderId": "1"
  }
}
```


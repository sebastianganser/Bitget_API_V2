---
conversion_date: "2025-03-12"
document_title: "Futures Transaction Records | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/tax/Get-Future-Account-Record"
---

# Futures Transaction Records | Bitget API

## Futures Transaction Records

**Frequency limit:** 1 times/1s (User ID)

### Description
Futures transaction records

### HTTP Request
```
GET /api/v2/tax/future-record
```

### Request Parameters
| Parameter     | Type   | Required | Description                                                                 |
|--------------|--------|----------|-----------------------------------------------------------------------------|
| productType  | String | No       | Product type (default: USDT-FUTURES)                                       |
|              |        |          | - USDT-FUTURES: USDT professional futures                                  |
|              |        |          | - COIN-FUTURES: Mixed futures                                              |
|              |        |          | - USDC-FUTURES: USDC professional futures                                  |
| marginCoin   | String | No       | Default all margin coin                                                    |
| startTime    | String | Yes      | Start time (timestamp in milliseconds)                                     |
| endTime      | String | Yes      | The maximum interval between startTime and endTime is 30 days.             |
| limit        | String | No       | Default: 500, maximum: 500                                                  |
| idLessThan   | String | No       | The last recorded ID                                                       |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/tax/future-record?startTime=1686" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameters
| Parameter       | Type   | Description                                              |
|----------------|--------|----------------------------------------------------------|
| id             | String | Transaction history ID                                   |
| symbol         | String | Symbol                                                   |
| marginCoin     | String | Margin coin                                              |
| futureTaxType  | String | Futures transaction type                                 |
| amount         | String | Quantity                                                 |
| fee            | String | Transaction fee                                          |
| ts             | String | When this record was generated, millisecond timestamp   |

### `futureTaxType` Values
- TRANSFER_IN: Fund transfer
- TRANSFER_OUT: Fund transfer
- ORDER_DEALT_FROZEN_OUT: Order dealt fund out
- ORDER_DEALT_IN: Order dealt fund in
- ORDER_PLF_FEE_OUT: Handling fee deduction
- EXCHANGE_SOURCE_TOKEN_USER_OUT: Redeem
- EXCHANGE_TARGET_TOKEN_USER_IN: Redeem
- OPEN_LONG: Open long
- OPEN_SHORT: Open short
- BUY_DEAL: Buy
- SELL_DEAL: Sell
- CLOSE_LONG: Close long
- CLOSE_SHORT: Close short
- FORCE_CLOSE_LONG: Forced reduction of long position
- FORCE_CLOSE_SHORT: Forced reduction of short position
- BURST_CLOSE_LONG: Liquidate long position
- BURST_CLOSE_SHORT: Liquidate short position
- OFFSET_REDUCE_CLOSE_LONG: Offset close long
- OFFSET_REDUCE_CLOSE_SHORT: Offset close short
- FORCE_BUY_SSM: Forced buy
- FORCE_SELL_SSM: Forced sell
- BURST_BUY_SSM: Liquidate buy
- BURST_SELL_SSM: Liquidate sell
- RISK_LIQ_USER_IN: User money in due to liquidation risk
- RISK_LIQ_USER_OUT: User money out due to liquidation risk
- INTEREST_SETTLEMENT_OUT: Interest deduction
- CONTRACT_MAIN_SETTLE_FEE_USER_IN: Funding fee collection
- CONTRACT_MAIN_SETTLE_FEE_USER_OUT: Funding fee deduction

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1687257612262,
    "data": [
        {
            "id": "1",
            "symbol": "TRXUSDT",
            "marginCoin": "USDT",
            "futureTaxType": "close_long",
            "amount": "0.10545",
            "fee": "-0.02134863",
            "ts": "1679909309766"
        }
    ]
}
```


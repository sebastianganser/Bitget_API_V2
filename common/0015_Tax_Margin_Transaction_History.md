---
conversion_date: "2025-03-12"
document_title: "Margin Transaction History | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/tax/Get-Margin-Account-Record"
---

# Margin Transaction History | Bitget API

## Margin Transaction History

**Frequency limit:** 1 times/1s (User ID)

### Description
Margin transaction records

### HTTP Request
```
GET /api/v2/tax/margin-record
```

### Request Parameters
| Parameter     | Type   | Required | Description                                                                 |
|---------------|--------|----------|-----------------------------------------------------------------------------|
| marginType    | String | No       | Leverage type<br>isolated: Isolated margin<br>crossed: Cross margin(default) |
| coin          | String | No       | Default all coin type                                                      |
| startTime     | String | Yes      | Start time (time stamp in milliseconds)                                   |
| endTime       | String | Yes      | The maximum interval between startTime and endTime (time stamp in milliseconds) is 30 days. |
| limit         | String | No       | Default: 500, maximum: 500                                                 |
| idLessThan    | String | No       | The last recorded ID                                                       |

### Request Example
```bash
curl "https://api.bitget.com/api/v2/tax/margin-record?startTime=168" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json"
```

### Response Parameters
| Parameter       | Type   | Description                                                                  |
|------------------|--------|------------------------------------------------------------------------------|
| id               | String | Record id                                                                   |
| coin             | String | Coin                                                                         |
| symbol           | String | Trade pair                                                                   |
| marginTaxType    | String | transfer_in: Inbound transfer<br>transfer_out: Outbound transfer<br>borrow: Borrowings<br>repay: Repayment<br>liquidation_fee: Liquidation fee<br>compensate: Risk fund compensation for collateral shortfall<br>deal_in: Margin buy<br>deal_out: Margin sell<br>interest_repay: Interest repayment<br>confiscated: Deducted for collateral shortfall<br>exchange_in: Conversion profit<br>exchange_out: Conversion profit |
| amount           | String | Quantity                                                                     |
| fee              | String | Transaction fee                                                              |
| total            | String | Total accounts                                                               |
| ts               | String | Record generation time, Unix millisecond timestamps                          |

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1687259242290,
    "data": [
        {
            "id": "1",
            "coin": "USDT",
            "marginTaxType": "transfer_in",
            "amount": "13333",
            "fee": "0",
            "total": "13333",
            "symbol": "BTCUSDT",
            "ts": "1686129284474"
        }
    ]
}
```


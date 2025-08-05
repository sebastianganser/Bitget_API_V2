---
conversion_date: "2025-03-12"
document_title: "P2P Transaction Records | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/tax/Get-P2P-Account-Record"
---

# P2P Transaction Records | Bitget API

## P2P Transaction Records

**Frequency limit:** 1 times/1s (User ID)

### Description
p2p transaction records

### HTTP Request
```
GET /api/v2/tax/p2p-record
```

### Request Parameters
| Parameter     | Type   | Required | Description                                                             |
|---------------|--------|----------|-------------------------------------------------------------------------|
| coin          | String | No       | Default all coin type                                                   |
| startTime     | String | Yes      | Start time (time stamp in milliseconds)                                 |
| endTime       | String | Yes      | The maximum interval between startTime and endTime (time stamp in milliseconds) is 30 days. |
| limit         | String | No       | Default: 500, maximum: 500                                              |
| idLessThan    | String | No       | The last recorded ID                                                    |

### Request Example
```
curl "https://api.bitget.com/api/v2/tax/p2p-record?startTime=16861 \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \
```

### Response Parameters
| Parameter     | Type   | Description           |
|---------------|--------|-----------------------|
| id            | String | Record id lastEndId   |
| coin          | String | Coin                  |
| p2pTaxType    | String | p2p taxation types    |
| total         | String | Total accounts        |

#### p2pTaxType values:
- `transfer_in`: Inbound transfer
- `transfer_out`: Outbound transfer
- `sell`: Sell
- `buy`: Buy

### Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1687260620793,
    "data": [
        {
            "id": "1752117",
            "coin": "USDT",
            "p2pTaxType": "buy",
            "total": "10",
            "ts": "1680582050393"
        }
    ]
}
```


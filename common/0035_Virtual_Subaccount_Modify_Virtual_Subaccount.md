---
conversion_date: "2025-03-12"
document_title: "Modify Virtual Subaccount | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/vsubaccount/Modify-Virtual-Subaccount"
---

# Modify Virtual Subaccount

**Frequency limit:** 5 times/1s (User ID)

## Description
Modify the virtual sub-account

## HTTP Request
```
POST /api/v2/user/modify-virtual-subaccount
```

## Request Parameters
| Parameter       | Type         | Required | Description                |
|----------------|--------------|----------|----------------------------|
| subAccountUid  | String       | Yes      | Sub-account Uid            |
| permList       | List<String> | Yes      | Permissions                |
|                |              |          | spot_trade – Spot trade    |
|                |              |          | contract_trade – Futures trade read-write |
|                |              |          | read – Read permissions    |
| status         | String       | Yes      | Sub-account status         |
|                |              |          | normal – Normal            |
|                |              |          | freeze – Freeze            |

## Request Example
```bash
curl -X POST "https://api.bitget.com/api/v2/user/modify-virtual-subaccount" \
   -H "ACCESS-KEY:*******" \
   -H "ACCESS-SIGN:*" \
   -H "ACCESS-PASSPHRASE:*" \
   -H "ACCESS-TIMESTAMP:1659076670000" \
   -H "locale:en-US" \
   -H "Content-Type: application/json" \  
   -d '{"subAccountUid": "1","permList":["spot_trade,contract_trade"], 
"status":"normal"}'
```

## Response Parameters
| Parameter | Type   | Description |
|-----------|--------|-------------|
| result    | String | Edit result |
|           |        | success – Success |
|           |        | failure – Failure |

## Response Example
```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1682660666458,
    "data": {
        "result": "success"
    }
}
```

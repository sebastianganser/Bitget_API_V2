---
conversion_date: "2025-03-12"
document_title: "Get spot fund flow | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/apidata/Get-Spot-Fund-Flow"
---

# Get spot fund flow | Bitget API

## Get spot fund flow

**Rate limit:** 1 req/1s (IP)

### Description

Get spot fund flow

### HTTP Request

```
GET /api/v2/spot/market/fund-flow
```

### Request Parameters

| Parameter | Type   | Required | Description                          |
|----------|--------|----------|--------------------------------------|
| symbol   | String | Yes      | Trading pairs, BTCUSDT              |
| period   | String | No       | Query period: 15m (default), 30m, 1h, 2h, 4h, 1d |

### Request Example

```
curl "https://api.bitget.com/api/v2/spot/market/fund-flow?symbol=BTCUSDT&period=1d"
```

### Response Parameters

| Parameter           | Type   | Description              |
|---------------------|--------|--------------------------|
| whaleBuyVolume      | String | Whale buy volume         |
| dolphinBuyVolume    | String | Dolphin Buy Volume       |
| fishBuyVolume       | String | Fish Buy Volume          |
| whaleSellVolume     | String | Whale Sell Volume        |
| dolphinSellVolume   | String | Dolphin Sell Volume      |
| fishSellVolume      | String | Fish Sell Volume         |
| whaleBuyRatio       | String | Whale Buy Ratio          |
| dolphinBuyRatio     | String | Dolphin Buy Ratio        |
| fishBuyRatio        | String | Fish Buy Ratio           |
| whaleSellRatio      | String | Whale Sell Ratio         |
| dolphinSellRatio    | String | Dolphin Sell Ratio       |
| fishSellRatio       | String | Fish Sell Ratio          |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1656589586807,
    "data": {
        "whaleBuyVolume": "50.901579",
        "dolphinBuyVolume": "1.506897",
        "fishBuyVolume": "0.529853",
        "whaleSellVolume": "50.635982",
        "dolphinSellVolume": "1.429034",
        "fishSellVolume": "0.344032",
        "whaleBuyRatio": "50.901579",
        "dolphinBuyRatio": "1.506897",
        "fishBuyRatio": "0.529853",
        "whaleSellRatio": "50.635982",
        "dolphinSellRatio": "1.429034",
        "fishSellRatio": "0.344032"
    }
}
```


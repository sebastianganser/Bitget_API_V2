---
conversion_date: "2025-03-11"
document_title: "Query Announcements | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/notice/Get-All-Notices"
---

# Query Announcements | Bitget API

## Query Announcements

**Frequency limit:** 20 times/1s (IP)

### Description

Search for announcements within one month.

### HTTP Request

```
GET /api/v2/public/annoucements
```

### Request Parameters

| Parameter  | Type   | Required | Description                                                                 |
|-----------|--------|----------|-----------------------------------------------------------------------------|
| annType   | String | No       | Announcement type:<br>- latest_news: Latest events<br>- coin_listings: New coin listings<br>- trading_competitions_promotions: Trading competitions and promotions<br>- maintenance_system_updates: maintenance/system upgrades<br>- symbol_delisting: Delisting information |
| startTime | String | No       | Start time of the query, Unix millisecond timestamp, e.g. `1690196141868`<br>Search by announcement time |
| endTime   | String | No       | End time of the query, Unix millisecond timestamp, e.g. `1690196141868`<br>Search by announcement time |
| language  | String | Yes      | Language type:<br>- zh_CN: Chinese<br>- en_US: English<br>Returns English if the language chosen is not supported |

### Request Example

```bash
curl "https://api.bitget.com/api/v2/public/annoucements?language=zh_CN"
```

### Response Parameters

| Parameter | Type   | Description                                         |
|----------|--------|-----------------------------------------------------|
| annId    | String | Announcement ID                                     |
| annTitle | String | Announcement title                                  |
| annDesc  | String | Announcement description                            |
| cTime    | String | Announcement creation time, Unix millisecond format |
| language | String | Language type                                       |
| annUrl   | String | Announcement URL                                    |

### Response Example

```json
{
    "code": "00000",
    "msg": "success",
    "requestTime": 1688008631614,
    "data": [
        {
            "annId": "1",
            "annTitle": "test0629",
            "annDesc": "Latest announcement",
            "cTime": "1688008040000",
            "language": "zh_CN",
            "annUrl": "https://www.bitget.com/zh_CN/support/articles/23685"
        }
    ]
}
```

---
conversion_date: "2025-03-24"
document_title: "Depth Channel | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/contract/websocket/public/Order-Book-Channel"
---

# Depth Channel

## Description

This is the channel to get the depth data.  
Default data push frequency for `books`, `books5`, `books15` is **150ms**.  
Default data push frequency for `books1`: **100ms**

- **books**: All levels of depth. First update pushed is full data: `snapshot`, and then push the update data: `update`
- **books1**: 1st level of depth. Push `snapshot` each time
- **books5**: 5 depth levels. Push `snapshot` each time
- **books15**: 15 depth levels. Push `snapshot` each time

## Checksum

This mechanism can assist users in checking the accuracy of depth (order book) data.

### Merging update data into snapshot

After subscribing to the channel (such as `books` 400 levels) of Order Book, the user first receives the initial snapshot of market depth. Afterwards, the incremental update is subsequently received. The user is responsible for updating the snapshot on the client side.

- If there are any levels with the same price from the updates, compare the amount with the snapshot order book:
  - If the amount is 0, delete this depth data.
  - If the amount changes, replace the depth data.
- If there is no level in the snapshot with the same price from the update, insert the update depth information into the snapshot sorted by price (bid in descending order, ask in ascending order).

### Calculate Checksum

Use the first 25 bids and asks in the local snapshot to build a string (where a colon connects the price and amount in an ask or a bid), and then calculate the CRC32 value (32-bit signed integer).

- When the bid and ask depth data exceed 25 levels, each of them will intercept 25 levels of data. The string to be checked is queued in a way that the bid and ask depth data are alternately arranged.  
  Example:  
  `bid1[price:amount]:ask1[price:amount]:bid2[price:amount]:ask2[price:amount]...`

- When the bid or ask depth data is less than 25 levels, the missing depth data will be ignored.  
  Example:  
  `bid1[price:amount]:ask1[price:amount]:ask2[price:amount]:ask3[price:amount]...`

- If price is `0.5000`, **DO NOT** calculate the checksum by `0.5`, **please DO use the original value**.

#### 1. More than 25 levels of bid and ask

A local snapshot of market depth (only 2 levels shown here, 25 levels should actually be used):

```json
"bids": [
  [ 43231.1, 4 ],   // bid1
  [ 43231,   6 ]    // bid2
],
"asks": [
  [ 43232.8, 9 ],   // ask1
  [ 43232.9, 8 ]    // ask2
]
```

Build the string to check CRC32:  
`"43231.1:4:43232.8:9:43231:6:43232.9:8"`

Sequence:  
`bid1[price:amount]:ask1[price:amount]:bid2[price:amount]:ask2[price:amount]`

#### 2. Less than 25 levels of bid or ask

A local snapshot of market depth:

```json
"bids": [
  [ 3366.1, 7 ] // bid1
],
"asks": [
  [ 3366.8, 9 ],    // ask1
  [ 3368  , 8 ],    // ask2
  [ 3372  , 8 ]     // ask3
]
```

Build the string to check CRC32:  
`"3366.1:7:3366.8:9:3368:8:3372:8"`

Sequence:  
`bid1[price:amount]:ask1[price:amount]:ask2[price:amount]:ask3[price:amount]`

---

## Request Parameters

| Parameter | Type         | Required | Description |
|----------|--------------|----------|-------------|
| op       | String       | Yes      | Operation, `subscribe` or `unsubscribe` |
| args     | List<Object> | Yes      | List of channels to request subscription |

Within `args`:

| Parameter  | Type   | Required | Description |
|------------|--------|----------|-------------|
| instType   | String | Yes      | Product type:<br>`USDT-FUTURES`, `COIN-FUTURES`, `USDC-FUTURES`, `SUSDT-FUTURES`, `SCOIN-FUTURES`, `SUSDC-FUTURES` |
| channel    | String | Yes      | Channel name: `books`, `books1`, `books5`, `books15` |
| instId     | String | Yes      | Product ID |

### Request Example

```json
{
    "op": "subscribe",
    "args": [
        {
            "instType": "USDT-FUTURES",
            "channel": "books5",
            "instId": "BTCUSDT"
        }
    ]
}
```

---

## Response Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| event     | String | Event |
| arg       | Object | Subscribed channels |
| msg       | String | Error message |
| code      | String | Error code (returned only on error) |

Within `arg`:

| Parameter  | Type   | Description |
|------------|--------|-------------|
| instType   | String | Product type (same as above) |
| channel    | String | Channel name |
| instId     | String | Product ID (e.g., ETHUSDT) |

### Response Example

```json
{
    "event": "subscribe",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "books5",
        "instId": "BTCUSDT"
    }
}
```

---

## Push Parameters

| Parameter | Type   | Description |
|-----------|--------|-------------|
| arg       | Object | Channels with successful subscription |

## Push Data

```json
{
    "action": "snapshot",
    "arg": {
        "instType": "USDT-FUTURES",
        "channel": "books5",
        "instId": "BTCUSDT"
    },
    "data": [
        {
            "asks": [
                [
                    "27000.5",
                    "8.760"
                ],
                [
                    "27001.0",
                    "0.400"
                ]
            ],
            "bids": [
                [
                    "27000.0",
                    "2.710"
                ],
                [
                    "26999.5",
                    "1.460"
                ]
            ],
            "checksum": 0,
            "ts": "1695716059516"
        }
    ],
    "ts": 1695716059516
}
```

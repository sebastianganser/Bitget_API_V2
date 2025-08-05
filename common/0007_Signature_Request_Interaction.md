---
conversion_date: "2025-03-11"
document_title: "Request Interaction | Bitget API"
extracted_urls:
  - "https://www.bitget.com/api-doc/common/signature-samaple/interaction"
  - "https://www.bitget.com/api-doc/spot/public/Get-Server-Time"
  - "https://www.bitget.com/api-doc/category/market-2"
---

# Request Interaction | Bitget API

## Request Interaction
All requests are based on the Https protocol, and the Content-Type in the POST request header should be set to: `application/json`.

### Request Interaction Description
- **Request parameters**: Encapsulate parameters according to the interface request parameters.
- **Submit request parameters**: Submit the encapsulated request parameters to the server through GET/POST.
- **Server Response**: The server first performs parameter security verification on the user request data, and returns the response data to the user in JSON format according to the business logic after passing the verification.
- **Data processing**: Process the server response data.

### Success
HTTP status code `200` indicates a successful response and may contain content. If the response contains content, it will be displayed in the corresponding return content.

### Common Error Codes
| Code | Description                                 |
|------|---------------------------------------------|
| 400  | Bad Request – Invalid request format        |
| 401  | Unauthorized – Invalid API Key              |
| 403  | Forbidden – You do not have access to the requested resource |
| 404  | Not Found – No request found                |
| 429  | Too Many Requests – Requests are too frequent and are limited by the system |
| 500  | Internal Server Error – We had a problem with our server |

*If it fails, the return body usually indicates the error message.*

## Standard Specification

### Timestamp
The unit of `ACCESS-TIMESTAMP` in the HTTP request signature is milliseconds. The timestamp of the request must be within 30 seconds of the API server time, otherwise the request will be considered expired and rejected. If there is a large deviation between the local server time and the API server time, we recommend that you compare the timestamp by querying the [API server time](https://www.bitget.com/api-doc/spot/public/Get-Server-Time).

### Frequency Limiting Rules
If the request is too frequent, the system will automatically limit the request and return the `429 Too Many Requests` status code.

- **Public interface**: For the market information interfaces, the unified rate limit is a maximum of 20 requests per second.
- **Authorization interface**: `apikey` is used to restrict the calling of authorization interfaces, refer to the frequency restriction rules of each interface for frequency restriction.

## Request Format
There are currently only two supported request methods: **GET** and **POST**

- **GET**: The parameters are transmitted to the server in the path through `queryString`.
- **POST**: The parameters are sent to the server in JSON format.

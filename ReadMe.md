# API General Info

The Secure Web APIs are designed to allow client applications to view and update data using the HTTPS(rest) and WSS(websocket)
protocol over the internet. The purpose of this document is to provide the urls and the specification of the messages
communicated through Web APIs.

## Message Format
All messages are in json format.

### Message Field Types
Type         | Description
------------ | ------------
Integer      | Integer numbers
Long         | Long numbers
Boolean      | True/False
DoubleString | Decimal numbers are returned as strings to preserve full precision across platforms
Enum         | Enum definition.  Passing invalid enum values will result in API_BAD_REQUEST error
String       | Text

## Timestamp
Unless otherwise specified, all timestamps returned from API are milliseconds since UNIX Epoch.

### Mandatory Field Indicators
Indicator    | Description
------------ | ----------------------------------------
M            | Mandatory field
(M)          | Mandatory field under certain conditions
O            | Optional field

# REST API General Info

## Base Url and Message Format

https://api.xxxx.com/

All requests and responses use application/json content type. Responses	follow HTTP response status codes to indicate
the success and the failure.

### Success/Error Response
Successful http response contains HTTP status code 200 and an optional body. If the response contains the body,
the fields within the body are documented in each related API sections.  Failed http response contains non 200 HTTP status
code and the body with an errorCode field to indicate the cause of the failures.

### Error Response Fields
Name         | Type        | Mandatory | Description
------------ | ------------| ----------| -----------------------------------------------------------------------------------------
errorCode    | String      | M         | Error code. e.g.INVALID_PASSWORD
errorData    | String      | O         | Additional information on the user data that may cause the error.  Data is provided in json format.

## Pagination
Pagination is supported for all REST calls that return arrays. The newest items are returned by default.

Name	   | Type(value)| Mandatory| Description
-----------| -----------|----------|-------------------
pageNumber | Integer    | O        | Default to 1
pageSize   | Integer    | O	       | Default to 100

Example: GET api/orders?pageNumber=1&pageSize=100

## Rate Limits

* Throttle public endpoints by IP: 5 requests per second
* Throttle authenticated endpoints by user ID: 5 requests per second
* Most endpoint request counts as one request. 
* For certain endpoint requests, each request counts as more than 1 due to extra system processing resources required.  The doc for such endpoints should contain the weight information which indicates the number of requests it counts for.
* When the rate limit is exceeded, a status of 429 will be returned.

# Websocket API General Info

wss://ws-api.xxxx.com

All messages sent and received through websocket are encoded in JSON
format. All messages have a **type** attribute that can be used to
handle the message.

Failures will cause an error message to be emitted with **errorCode**.

### Error Response Fields
Name          | Type(value) | Mandatory |Description
--------------|-------------|-----------|---------------------------
type          | error       | M         | Error message type
userMessageId |	Integer	    |(M)	    | Mandatory if userMessageId is provided in the user request
errorCode	  | String      | M	        | Error code

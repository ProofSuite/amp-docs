# HTTP API



{% hint style="info" %}
See the Websocket API section on how to create and cancel orders. We are currently working adding HTTP methods for creating and canceling orders.
{% endhint %}

## TOKENS

{% api-method method="get" host="https://amp.exchange/api" path="/tokens/base" %}
{% api-method-summary %}
Get Base Tokens
{% endapi-method-summary %}

{% api-method-description %}
This endpoints queries all base tokens currently registered on the AMP exchange
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="listed" type="boolean" %}
Returns listed tokens if set to true and unlisted tokens \("non-official"\) tokens if set to false.  
If omitted, this endpoint will return all base tokens
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```javascript
{
    "name": "Cake's name",
    "recipe": "Cake's recipe name",
    "cake": "Binary cake"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```javascript
{
    "message": "Ain't no cake like that."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange" path="/tokens/quote" %}
{% api-method-summary %}
Get Quote Tokens
{% endapi-method-summary %}

{% api-method-description %}
This endpoint queries all quote tokens currently registered on the AMP exchange
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange/api" path="/tokens" %}
{% api-method-summary %}
Get Token
{% endapi-method-summary %}

{% api-method-description %}
This endpoint queries a token by token address
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="address" type="string" required=true %}
Token Ethereum Contract Address. Must start with "0x"
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange/api" path="/tokens" %}
{% api-method-summary %}
Get Tokens
{% endapi-method-summary %}

{% api-method-description %}
This endpoints queries and returns all tokens currently registered on the AMP exchange
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="listed" type="boolean" required=false %}
Returns listed tokens if set to true and unlisted tokens \("non-official"\) tokens if set to false.  
If omitted, this endpoint will return all tokens.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## PAIRS

{% api-method method="get" host="https://amp.exchange/api" path="/pair" %}
{% api-method-summary %}
Get Pair
{% endapi-method-summary %}

{% api-method-description %}
This endpoints returns pair information for a given base token address and quote token address
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="baseToken" type="string" required=true %}
Base Token Contract Address. Must start with 0x
{% endapi-method-parameter %}

{% api-method-parameter name="quoteToken" type="string" required=true %}
Quote Token Contract Address. Must start with 0x
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.expchange/api" path="/pairs" %}
{% api-method-summary %}
Get Pairs
{% endapi-method-summary %}

{% api-method-description %}
This endpoint return the pair information for all pairs registered on the AMP exchange
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}
Returns listed tokens if set to true and unlisted pairs \("non-official"\) pairs if set to false. If omitted, the query will return all pairs. 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.expchange/api" path="/pairs/data" %}
{% api-method-summary %}
Get Pair Data
{% endapi-method-summary %}

{% api-method-description %}
The _**Get Pair Data**_ endpoint returns the recent pair trading data. It is possible to query a simplified version of the data or the exact numbers.   
  
The _**simple**_ pair data is returned as numbers. The _**exact**_ data is returned as strings because the exact numbers are too big to be contained safely in javascript Number types.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="simple" type="boolean" required=false %}
If simple is set to true, a simplified version of token pair data will be returned
{% endapi-method-parameter %}

{% api-method-parameter name="exact" type="boolean" required=false %}
If exact is set to true, an exact version of token pair data will be returned. Both "simple" and "exact" can not be included in the same query
{% endapi-method-parameter %}

{% api-method-parameter name="quoteToken" type="string" required=false %}
Quote Token Smart Contract Address. If both quoteToken and baseToken params parameters are missing, data for all token pairs will be returned.
{% endapi-method-parameter %}

{% api-method-parameter name="baseToken" type="string" required=false %}
Base Token Smart Contract Address
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://amp.expchange/api" path="/pairs/create" %}
{% api-method-summary %}
Create Pairs
{% endapi-method-summary %}

{% api-method-description %}
The _**Create Pairs**_ endpoint takes the address of an ERC20 token and creates token pairs with all quote tokens that are currently listed on the AMP exchange.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-form-data-parameters %}
{% api-method-parameter name="" type="string" required=false %}
  
  
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## ORDERS

{% hint style="info" %}
There is currently no HTTP for placing orders. See Websocket API section for how to place orders.
{% endhint %}

{% api-method method="get" host="https://amp.exchange/api" path="/orders" %}
{% api-method-summary %}
Get Orders
{% endapi-method-summary %}

{% api-method-description %}
The _**Get Orders**_ endpoint returns the list of orders for a given Ethereum address
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="limit" type="number" required=false %}
Maximum number of orders to be queried
{% endapi-method-parameter %}

{% api-method-parameter name="address" type="string" required=true %}
Ethereum account address. Must start with "0x"
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange/api" path="/orders/history" %}
{% api-method-summary %}
 Get Order History
{% endapi-method-summary %}

{% api-method-description %}
The _**Get Orders History**_ endpoint returns the **"CANCELED"** or **"FILLED"** orders for a given Ethereum address.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="address" type="string" required=true %}
Ethereum account address. Must start with "0x"
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
Maximum number of orders to be queried
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange/api" path="/orders/positions" %}
{% api-method-summary %}
Get Current Orders
{% endapi-method-summary %}

{% api-method-description %}
The _**Get Current Orders**_ endpoint returns **"OPEN"** and **"PARTIALLY\_FILLED"** orders for a given Ethereum address. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="address" type="string" required=true %}
Ethereum account address. Must start with "0x"
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="string" required=false %}
Maximum number of orders to be queried
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## TRADES

{% api-method method="get" host="https://amp.exchange/api" path="/trades" %}
{% api-method-summary %}
Get User Trades
{% endapi-method-summary %}

{% api-method-description %}
The **Get User Trades** endpoint returns trades for a given user \(Ethereum address\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="address" type="string" required=true %}
Ethereum account address. Must start with "0x"
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
Maximum number of trades to be queried
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange/api" path="/trades/pair" %}
{% api-method-summary %}
Get Pair Trades
{% endapi-method-summary %}

{% api-method-description %}
The _**Get Trades History**_ endpoint returns trades for a given token pair.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="baseToken" type="string" required=false %}
Base Token Contract Address
{% endapi-method-parameter %}

{% api-method-parameter name="quoteToken" type="string" required=false %}
Quote Token Contract Address
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" required=false %}
Maximum number of trades to be queried
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## ORDER BOOK

{% api-method method="get" host="https://amp.exchange/api" path="/orderbook" %}
{% api-method-summary %}
Get Order Book
{% endapi-method-summary %}

{% api-method-description %}
The Get OrderBook endpoint returns the AMP exchange orderbook for a given pair. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="baseToken" type="string" required=false %}
Base Token Contract Address
{% endapi-method-parameter %}

{% api-method-parameter name="quoteToken" type="string" required=false %}
Quote Token Contract Address
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange/api" path="/orderbook/raw" %}
{% api-method-summary %}
Get Raw Order Book
{% endapi-method-summary %}

{% api-method-description %}
The _**Get Raw OrderBook**_ endpoint returns the AMP exchange raw order book for a given pair. The Raw OrderBook is a list of raw orders that include the exact numbers to be used with the exchange smart contracts as well as signatures, etc. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## INFO

{% api-method method="get" host="https://amp.expchange/api" path="/info" %}
{% api-method-summary %}
Get Info
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.expchange/api" path="/info/exchange" %}
{% api-method-summary %}
Get Exchange Info
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.expchange/api" path="/info/fees" %}
{% api-method-summary %}
Get Fees Info
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://amp.exchange/api" path="/info/operators" %}
{% api-method-summary %}
Get Operators Info
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## STATS

{% api-method method="get" host="https://amp.exchange/api" path="/stats/trading" %}
{% api-method-summary %}
Get Trading Stats
{% endapi-method-summary %}

{% api-method-description %}
This endpoints queries AMP recent trading statistics
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## OHLCV

{% api-method method="get" host="https://amp.exchange/api" path="/ohlcv" %}
{% api-method-summary %}
Get OHLCV
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="baseToken" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="quoteToken" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="pairName" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="duration" type="number" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="unit" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="from" type="integer" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="to" type="integer" required=false %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}












# Resources

This describes API resource fetching via HTTPS calls.

## `/status`

```shell
curl -X POST 'https://api.livecoinwatch.com/status' \
  -H 'content-type: application/json'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/status'), {
  method: 'POST',
  headers: new Headers({ 'content-type': 'application/json' })
})
```

> ...and it returns nothing! Well, empty JSON object anyways.

With this, find out is everything fine with the API. It is also only end-point that doesn't require `x-api-key` header.

### Request

Accepts no request parameters.

### Response

Ideally, responds with nothing which means everything is hopefully running fine. One of the [errors](#errors) objects otherwise.

## `/credits`

```shell
curl -X POST 'https://api.livecoinwatch.com/credits' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/credits'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  })
})
```

> Let's see how much credits we have and what's the limit:

```json
{
  "dailyCreditsLimit": 10000,
  "dailyCreditsRemaining": 4321
}
```

> Error response (one of):

```json
{
  "error": {
    "code": 401,
    "status": "Unauthorized",
    "description": "Your API key is wrong."
  }
}
```

Through this end-point, you can find out your API key related information.

### Request

Accepts no request parameters.

### Response

key | type | description
--- | ---- | -----------
`dailyCreditsLimit` | number | total daily starting credits
`dailyCreditsRemaining` | number | remaining daily credits

## `/overview`

Get current aggregated data for all coins.

```shell
curl -X POST 'https://api.livecoinwatch.com/overview' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD"}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/overview'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({ currency: 'USD' })
})
```

> How's all of crypto doing at the moment:

```json
{
  "cap": 1810888785486,
  "volume": 70194520152,
  "liquidity": 3934498354,
  "btcDominance": 0.5932948858748709
}
```

### Request

key | type | description
--- | ---- | -----------
`currency` | string | any valid coin or fiat code

### Response

key | type | description
--- | ---- | -----------
`cap` | number | market cap of all coins
`volume` | number | volume of all coins
`liquidity` | number | 2% liquidity of all coins
`btcDominance` | number | percentage of BTC cap in total market cap

## `/overview/history`

Get historical aggregated data of entire market.

```shell
curl -X POST'https://api.livecoinwatch.com/overview/history' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","start":1606232700000,"end":1606233000000}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/overview/history'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({
    currency: 'USD',
    start: 1606232700000,
    end: 1606233000000
  })
})
```

> How's all of crypto trending across time:

```json
[
  {
    "date": 1606232700000,
    "cap": 581093086830,
    "volume": 56386526334,
    "liquidity": 1288814828,
    "btcDominance": 0.614520121091147
  },
  {
    "date": 1606233000000,
    "cap": 582164608234,
    "volume": 56939433331,
    "liquidity": 1274915303,
    "btcDominance": 0.612858305207367
  }
]
```

### Request

key | type | description
--- | ---- | -----------
`currency` | string | any valid coin or fiat code
`start` | number | UNIX timestamp in milliseconds of time interval start
`end` | number | UNIX timestamp in milliseconds of time interval end

### Response

key | type | description
--- | ---- | -----------
`date` | number | UNIX timestamp in milliseconds of datapoint
`cap` | number | market cap of all coins
`volume` | number | volume of all coins
`liquidity` | number | 2% liquidity of all coins
`btcDominance` | number | percentage of BTC cap in total market cap

## `/coins/single`

All information about a single coin at latest moment in time.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/single' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","code":"ETH","meta":true}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/coins/single'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({
    currency: 'USD',
    code: 'ETH',
    meta: true
  })
})
```

> Let's see all of current data on ETH, in USD currency:

```json
{
  "name": "Ethereum",
  "symbol": "Ξ",
  "color": "#282a2a",
  "png32": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/32/eth.png",
  "png64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/64/eth.png",
  "webp32": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/32/eth.webp",
  "webp64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/64/eth.webp",
  "exchanges": 153,
  "markets": 3717,
  "pairs": 1773,
  "allTimeHighUSD": 2036.3088032624153,
  "circulatingSupply": 115250583,
  "totalSupply": null,
  "maxSupply": null,
  "rate": 1786.6742250505124,
  "volume": 11522748696,
  "cap": 205915246068
}
```

### Request

key | type | description
--- | ---- | -----------
`code` | string | coin code
`currency` | string | any valid coin or fiat code
`meta` | boolean | to include full coin information or not

### Response

key | type | description
--- | ---- | -----------
`name` | string | coin's name
`symbol` | string | coin's symbol
`color` | string | hexadecimal color code (`#282a2a`)
`png32` | string | 32-pixel png image of coin icon
`png64` | string | 64-pixel png image of coin icon
`webp32` | string | 32-pixel webp image of coin icon
`webp64` | string | 64-pixel webpg image of coin icon
`exchanges` | number | number of exchange coin is present at
`markets` | number | number of markets coin is present at
`pairs` | number | number of unique markets coin is present at
`allTimeHighUSD` | number | all-time high in USD
`circulatingSupply` | number | number of coins minted, but not locked
`totalSupply` | number | number of coins minted, including locked
`maxSupply` | number | maximum number of coins that can be minted
`rate` | number | price of coin in requested currency
`volume` | number | reported trading volume of the coin in last 24 hours in requested currency
`cap` | number | coin's market cap in requested currency
`totalCap` | number | coin's hypothetical total capitalization at the moment


## `/coins/single/history`

Historical values for coin.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/single/history' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","code":"BTC","start":1617035100000,"end":1617035400000,"meta":true}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/coins/single/history'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({
    currency: 'USD',
    code: 'BTC',
    start: 1617035100000,
    end: 1617035400000,
    meta: true
  })
})
```

> How is BTC trending over a period of time:

```json
{
  "code": "BTC",
  "name": "Bitcoin",
  "symbol": "₿",
  "color": "#fa9e32",
  "png32": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/32/btc.png",
  "png64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/64/btc.png",
  "webp32": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/32/btc.webp",
  "webp64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/production/currencies/64/btc.webp",
  "exchanges": 145,
  "markets": 4180,
  "pairs": 1524,
  "allTimeHighUSD": 61518.797756895845,
  "circulatingSupply": 18669593,
  "totalSupply": null,
  "maxSupply": 21000000,
  "history": [
    {
      "date": 1617035100000,
      "rate": 57372.11890245088,
      "volume": 21800580671,
      "cap": 1071017666924
    },
    {
      "date": 1617035400000,
      "rate": 57521.9764455523,
      "volume": 21852737676,
      "cap": 1073815194352
    }
  ]
}
```

### Request

key | type | description
--- | ---- | -----------
`currency` | string | any valid coin or fiat code
`code` | string | coin code
`start` | number | UNIX timestamp in milliseconds of time interval start
`end` | number | UNIX timestamp in milliseconds of time interval end
`meta` | boolean | to include full coin information or not

### Response

key | type | description
--- | ---- | -----------
`code` | string | coin's own code
`name` | string | coin's name
`symbol` | string | coin's symbol
`color` | string | hexadecimal color code (`#282a2a`)
`png32` | string | 32-pixel png image of coin icon
`png64` | string | 64-pixel png image of coin icon
`webp32` | string | 32-pixel webp image of coin icon
`webp64` | string | 64-pixel webpg image of coin icon
`exchanges` | number | number of exchange coin is present at
`markets` | number | number of markets coin is present at
`pairs` | number | number of unique markets coin is present at
`allTimeHighUSD` | number | all-time high in USD
`circulatingSupply` | number | number of coins minted, but not locked
`totalSupply` | number | number of coins minted, including locked
`maxSupply` | number | maximum number of coins that can be minted
`history` | array | list of `date`, `rate`, `volume` and `cap`

## `/coins/list`

Assorted information for a list of coins.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/list' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","limit":2,"sort":"rank","order":"ascending","meta":false}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/coins/list'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({
    currency: 'USD',
    limit: 2,
    sort: 'rank',
    order: 'ascending',
    meta: false
  })
})
```

> Let's see top two coins by rank, just frequently-changing data, please:

```json
[
  {
    "code": "BTC",
    "rate": 59075.58195922644,
    "volume": 23100393182,
    "cap": 1102979514307,
    "maxCap": 1240587221143.7551
  },
  {
    "code": "ETH",
    "rate": 1933.6392223621567,
    "volume": 12686119704,
    "cap": 222928063223
  }
]
```

### Request

key | type | description
--- | ---- | -----------
`currency` | string | any valid coin or fiat code
`sort` | string | sorting parameter, `rank`, `price`, `volume`, `code`, `name`
`order` | string | sorting order, `ascending` or `descending`
`offset` | number | offset of the list, default `0`
`limit` | number | limit of the list, default `10`, maximum `100`
`meta` | boolean | to include full coin information or not

### Response

key | type | description
--- | ---- | -----------
`code` | string | coin's code
`name` | string | coin's name
`symbol` | string | coin's symbol
`color` | string | hexadecimal color code (`#282a2a`)
`png32` | string | 32-pixel png image of coin icon
`png64` | string | 64-pixel png image of coin icon
`webp32` | string | 32-pixel webp image of coin icon
`webp64` | string | 64-pixel webpg image of coin icon
`exchanges` | number | number of exchange coin is present at
`markets` | number | number of markets coin is present at
`pairs` | number | number of unique markets coin is present at
`allTimeHighUSD` | number | all-time high in USD
`circulatingSupply` | number | number of coins minted, but not locked
`totalSupply` | number | number of coins minted, including locked
`maxSupply` | number | maximum number of coins that can be minted
`rate` | number | coin rate in the specified currency
`volume` | number | 24-hour volume of coin
`cap` | number | market cap of coin

## `/fiats/all`

List of all the fiats.

```shell
curl -X POST 'https://api.livecoinwatch.com/fiats/all' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/fiats/all'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  })
})
```

> Array of all the fiat currencies supported:

```json
[
  {
    "code": "ALL",
    "countries": [ "ALB" ],
    "flag": "ALB",
    "name": "Albanian Lek",
    "symbol": "Lek"
  },
  {
    "code": "HNL",
    "countries": [ "HND" ],
    "flag": "HND",
    "name": "Honduran Lempira",
    "symbol": "L"
  },
  ...
]
```

### Request

Accepts no request parameters.

### Response

An array of following:

key | type | description
--- | ---- | -----------
`code` | string | fiat ISO code
`name` | string | fiat name
`symbol` | string | fiat symbol
`countries` | array | ISO country code list
`flag` | string | ISO country code of the flag

## `/exchanges/single`

Assorted exchange information.

```shell
curl -X POST 'https://api.livecoinwatch.com/exchanges/single/meta' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"ETH","code":"gemini","meta":true}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/exchanges/single'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({
    currency: 'ETH',
    code: 'gemini',
    meta: true
  })
})
```

> Should get us all the information we have on Gemini exchange:

```json
{
  "code": "gemini",
  "name": "Gemini",
  "png64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/gemini.png",
  "png128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/gemini.png",
  "webp64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/gemini.webp",
  "webp128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/gemini.webp",
  "centralized": true,
  "usCompliant": true,
  "markets": 43,
  "volume": 115473.97264617922,
  "depth": 23151.76758456139,
  "bidTotal": 10968.751251210175,
  "askTotal": 12183.016333351212,
  "visitors": 31738,
  "volumePerVisitor": 3.638350641066835
}
```

### Request

key | type | description
--- | ---- | -----------
`currency` | string | any valid coin or fiat code
`code` | string | exchange code
`meta` | boolean | to include full exchange information or not

### Response

key | type | description
--- | ---- | -----------
`code` | string | exchange code
`name` | string | exchange name
`png32` | string | 32-pixel png image of exchange icon
`png64` | string | 64-pixel png image of exchange icon
`webp32` | string | 32-pixel webp image of exchange icon
`webp64` | string | 64-pixel webpg image of exchange icon
`centralized` | boolean | is the exchange centralized or decentralized
`usCompliant` | boolean | is the exchange compliant in the USA
`markets` | number | count of currently active markets on the exchange
`volume` | number | 24-hour volume in specified currency
`depth` | number | 2% orderbook total depth
`bidTotal` | number | 2% orderbook value bids
`askTotal` | number | 2% orderbook value asks
`visitors` | number | number of daily visitors, estimate
`volumePerVisitor`| number | daily volume per daily visitor


## `/exchanges/list`

Assorted information on list of exchanges.

```shell
curl -X POST 'https://api.livecoinwatch.com/exchanges/single' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","limit":1,"sort":"visitors","order":"descending","meta":true}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/exchanges/single'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({
    currency: 'USD',
    limit: 1,
    sort: 'visitors',
    order: 'descending',
    meta: true
  })
})
```

> Top one exchange by number of visitors:

```json
[
  {
    "code": "binance",
    "name": "Binance",
    "png64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/binance.png",
    "png128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/binance.png",
    "webp64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/binance.webp",
    "webp128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/binance.webp",
    "centralized": true,
    "usCompliant": true,
    "markets": 935,
    "volume": 27523372418,
    "depth": 465190859.1170668,
    "bidTotal": 225078060.0687528,
    "askTotal": 240112799.048314,
    "visitors": 779440,
    "volumePerVisitor": 35311.72690393103
  }
]
```

### Request

key | type | description
--- | ---- | -----------
`code` | string | exchange code
`sort` | string | sorting parameter, `volume`, `liquidity`, `code`, `name`
`order` | string | sorting order, `ascending` or `descending`
`offset` | number | offset of the list, default `0`
`limit` | number | limit of the list, default `50`, maximum `100`
`meta` | boolean | to include full exchange information or not

### Response

Returns array of objects containing:

key | type | description
--- | ---- | -----------
`code` | string | exchange code
`name` | string | exchange name
`png32` | string | 32-pixel png image of exchange icon
`png64` | string | 64-pixel png image of exchange icon
`webp32` | string | 32-pixel webp image of exchange icon
`webp64` | string | 64-pixel webpg image of exchange icon
`centralized` | boolean | is the exchange centralized or decentralized
`usCompliant` | boolean | is the exchange compliant in the USA
`markets` | number | count of currently active markets on the exchange
`volume` | number | 24-hour volume in specified currency
`depth` | number | 2% orderbook total depth
`bidTotal` | number | 2% orderbook value bids
`askTotal` | number | 2% orderbook value asks
`visitors` | number | number of daily visitors, estimate
`volumePerVisitor`| number | daily volume per daily visitor


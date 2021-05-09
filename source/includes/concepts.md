# Concepts

We've tried to keep the API surface simple and efficient, so let's discuss few [concepts](#concepts) that apply to the entirety of the API.

## There Is Only One **Domain**

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

```php
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/status', 'r', false, $context);
print_r(stream_get_contents($fp));
```

> If everything's fine, you should get...

```json
{}
```

> ...bag of nothing, that's right! On the other hand, if something's wrong, you should get some kind of error:

```json
{
  "error": {
    "code": 503,
    "status": "Service unavailable.",
    "description": "We're temporarily offline for maintenance. Please try again later."
  }
}
```

Everything runs from a single domain, and that is `api.livecoinwatch.com`. All your HTTPS requests go there.

Try running code examples and see for yourself.

## There Is Only One **Key**

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

```php
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n"
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/credits', 'r', false, $context);
print_r(stream_get_contents($fp));
```

> Don't forget to replace `<YOUR_API_KEY>` with one you've got. Return response should be:

```json
{
  "dailyCreditsRemaining": 4321,
  "dailyCreditsLimit": 10000
  
}
```

Live Coin Watch uses API keys to access all end-points. You can generate a new API key at your [profile page](https://www.livecoinwatch.com/profile). Authorizing with your API key is as simple as providing HTTP header `x-api-key: <YOUR_API_KEY>`.

All ([but one](#status)) API end-points need to include this header.

You can only ever have one active key, but you can regenerate that one, in the case you lose it or you don't trust it being secret anymore.

Keep the key somewhere private, safe & handy.

<aside class="notice">
Astute reader will notice that, by having multiple profiles, they will effectively have more than one key. They would be correct.
</aside>

## There Is Only One **Method**

```shell
curl 'https://api.livecoinwatch.com/status' \
  -H 'content-type: application/json'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/status'), {
  method: 'GET',
  headers: new Headers({ 'content-type': 'application/json' })
})
```

```php
$context_options = array (
    'http' => array (
        'method' => 'GET',
        'header' => "Content-type: application/json\r\n"
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/status', 'r', false, $context);
print_r(stream_get_contents($fp));
```

> This will fail with:

```json
{
  "error": {
    "code": 405,
    "status": "Method Not Available.",
    "description": "You tried to access a resource with an invalid method."
  }
}
```

`POST` is the only method available to all the API calls.

## There Is Only One **Format**

Both requests and responses are in the form of JSON, so make sure to have `content-type: application/json` as well as `accept: application/json` headers where [environment](#environments) demands.

JSON in and JSON out, as simple as that.

That includes [errors](#errors) as well.

## There Is Only One **Currency**

Each API call response will only ever be in a single currency - the one you specified in your HTTPS request.

It can be *any* fiat currency or active cryptocurrency.

<!-- For your convenience, that currency will be reflected in the response. -->

By default, it will be `USD`.

<aside class="notice">
Note that this doesn't prevent you from making any or all of the API calls in different currency.
</aside>

## There Is Only One **Version**

There is only one publicly available version of the API.

[Watch this repository](https://github.com/LiveCoinWatch/lcw-api-docs)! It'll always update before the actual API updates.

## There Is Only One **Limit**

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

```php
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n"
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/credits', 'r', false, $context);
print_r(stream_get_contents($fp));
```

> Don't forget to replace `<YOUR_API_KEY>` with one you've got. Return response should be:

```json
{
  "dailyCreditsRemaining": 4321,
  "dailyCreditsLimit": 100000
}
```

Let's call it *credits*, and you can read about them [in detail](#limits), but summarized - they map directly to your requests 1-to-1.

You can always easily check your credits status at `/credits` end-point, as well as on your Live Coin Watch [profile page](https://www.livecoinwatch.com/profile).

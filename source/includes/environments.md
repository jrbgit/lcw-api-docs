# Environments

If you're interested in only exploring the API, there's not better place than [API playground](https://www.livecoinwatch.com/tools/api), in which case you can ignore this chapter.

The following are environments we officialy support, though you're welcome to write-up a wrapper - it's all simple and standard protocols really. Be sure to [let us know about it](mailto:contact+api@livecoinwatch.com), so we can maybe include it in the documentation!

## Shell

```shell
curl -X POST https://api.livecoinwatch.com \
  -H 'content-type: application/json'
```

For just exploring and playing around with the API, this might be the simplest option. All examples should run in most shells, as the only command used is the [all-mighty cURL](https://curl.haxx.se/).

<aside class="success">
Developers recommend using <a href="https://stedolan.github.io/jq/" target='_blank'>jq</a> in the pipeline, at least for pretty printing of responses.
</aside>


## JavaScript

```javascript
await fetch(new Request('https://api.livecoinwatch.com'), {
  method: 'POST',
  headers: new Headers({ 'content-type': 'application/json' })
})
```

All the examples are written for modern browers.

Most examples should be easily portable to run in other JavaScript environments like [Node.js](https://nodejs.org/en/about/releases/) or not even needing any changes from browser version with [Deno](https://deno.land).


## PHP

```php
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com', 'r', false, $context);
print_r(stream_get_contents($fp));
```

All PHP examples are written using pure PHP without using any dependencies. These examples should work on versions of PHP that support [stream_context_create](https://www.php.net/manual/en/function.stream-context-create.php) & [stream_get_contents](https://www.php.net/manual/en/function.stream-get-contents.php) (Supported versions: PHP 5, PHP 7, PHP 8).


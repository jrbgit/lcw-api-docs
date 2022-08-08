# Resources

This describes API resource fetching via HTTPS calls.

## `/status`

```shell
curl -X POST 'https://api.livecoinwatch.com/status' \
  -H 'content-type: application/json'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/status"), {
  method: "POST",
  headers: new Headers({ "content-type": "application/json" }),
});
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/status")
  .header("content-type", "application/json")
  .asString();
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/status"
  method := "POST"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/status"

payload={}
headers = {
  'content-type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/status")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")

request.httpMethod = "POST"

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/status")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"

response = https.request(request)
puts response.read_body
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/status");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
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
await fetch(new Request("https://api.livecoinwatch.com/credits"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
});
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/credits")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .asString();
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/credits");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/credits"
  method := "POST"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/credits")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/credits"

payload={}
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
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

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/credits")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"

response = https.request(request)
puts response.read_body
```

> Let's see how much credits we have and what's the limit:

```json
{
  "dailyCreditsRemaining": 4321,
  "dailyCreditsLimit": 10000
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

| key                     | type   | description                  |
| ----------------------- | ------ | ---------------------------- |
| `dailyCreditsRemaining` | number | remaining daily credits      |
| `dailyCreditsLimit`     | number | total daily starting credits |

## `/overview`

Get current aggregated data for all coins.

```shell
curl -X POST 'https://api.livecoinwatch.com/overview' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD"}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/overview"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({ currency: "USD" }),
});
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"USD\"\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/overview")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/overview")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"USD\"\n}")
  .asString();
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/overview"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "USD"
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/overview");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""USD""" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/overview"

payload = json.dumps({
  "currency": "USD"
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'USD'));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/overview', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/overview")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "USD"
})

response = https.request(request)
puts response.read_body
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

| key        | type   | description                 |
| ---------- | ------ | --------------------------- |
| `currency` | string | any valid coin or fiat code |

### Response

| key            | type   | description                               |
| -------------- | ------ | ----------------------------------------- |
| `cap`          | number | market cap of all coins                   |
| `volume`       | number | volume of all coins                       |
| `liquidity`    | number | ±2% liquidity of all coins                 |
| `btcDominance` | number | percentage of BTC cap in total market cap |

## `/overview/history`

Get historical aggregated data of entire market.

```shell
curl -X POST 'https://api.livecoinwatch.com/overview/history' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","start":1606232700000,"end":1606233000000}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/overview/history"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({
    currency: "USD",
    start: 1606232700000,
    end: 1606233000000,
  }),
});
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"USD\",\n\t\"start\": 1606232700000,\n\t\"end\": 1606233000000\n}\n"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/overview/history")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/overview/history")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"USD\",\n\t\"start\": 1606232700000,\n\t\"end\": 1606233000000\n}\n")
  .asString();
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/overview/history"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "USD",
	"start": 1606232700000,
	"end": 1606233000000
}
`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/overview/history");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""USD""," + "\n" +
@"	""start"": 1606232700000," + "\n" +
@"	""end"": 1606233000000" + "\n" +
@"}" + "\n" +
@"";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/overview/history"

payload = json.dumps({
  "currency": "USD",
  "start": 1606232700000,
  "end": 1606233000000
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'USD', 'start' => 1606232700000, 'end' => 1606233000000));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/overview/history', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/overview/history")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "USD",
  "start": 1606232700000,
  "end": 1606233000000
})

response = https.request(request)
puts response.read_body
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

| key        | type   | description                                           |
| ---------- | ------ | ----------------------------------------------------- |
| `currency` | string | any valid coin or fiat code                           |
| `start`    | number | UNIX timestamp in milliseconds of time interval start |
| `end`      | number | UNIX timestamp in milliseconds of time interval end   |

### Response

| key            | type   | description                                 |
| -------------- | ------ | ------------------------------------------- |
| `date`         | number | UNIX timestamp in milliseconds of datapoint |
| `cap`          | number | market cap of all coins                     |
| `volume`       | number | volume of all coins                         |
| `liquidity`    | number | ±2% liquidity of all coins                   |
| `btcDominance` | number | percentage of BTC cap in total market cap   |

## `/coins/single`

All information about a single coin at latest moment in time.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/single' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","code":"ETH","meta":true}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/coins/single"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({
    currency: "USD",
    code: "ETH",
    meta: true,
  }),
});
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/coins/single")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"USD\",\n\t\"code\": \"ETH\",\n\t\"meta\": true\n}")
  .asString();
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"USD\",\n\t\"code\": \"ETH\",\n\t\"meta\": true\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/coins/single")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/coins/single"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "USD",
	"code": "ETH",
	"meta": true
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/coins/single");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""USD""," + "\n" +
@"	""code"": ""ETH""," + "\n" +
@"	""meta"": true" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/coins/single"

payload = json.dumps({
  "currency": "USD",
  "code": "ETH",
  "meta": True
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'USD', 'code' => 'ETH', 'meta' => true));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/coins/single', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/coins/single")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "USD",
  "code": "ETH",
  "meta": true
})

response = https.request(request)
puts response.read_body
```

> Let's see all of current data on ETH, in USD currency:

```json
{
  "name": "Ethereum",
  "symbol": "Ξ",
  "rank": 2,
  "age": 2411,
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
  "cap": 205915246068,
  "delta": {
    "hour": 1.008,
    "day": 1.0808,
    "week": 1.2793,
    "month": 1.4754,
    "quarter": 0.4804,
    "year": 0.7455
  }
}
```

### Request

| key        | type    | description                             |
| ---------- | ------- | --------------------------------------- |
| `currency` | string  | any valid coin or fiat code             |
| `code`     | string  | coin code                               |
| `meta`     | boolean | to include full coin information or not |

### Response

| key                 | type   | description                                                                |
| ------------------- | ------ | -------------------------------------------------------------------------- |
| `name`              | string | coin's name                                                                |
| `symbol`            | string | coin's symbol                                                              |
| `rank`              | number | coin's rank                                                                |
| `age`               | number | coin's age in days                                                         |
| `color`             | string | hexadecimal color code (`#282a2a`)                                         |
| `png32`             | string | 32-pixel png image of coin icon                                            |
| `png64`             | string | 64-pixel png image of coin icon                                            |
| `webp32`            | string | 32-pixel webp image of coin icon                                           |
| `webp64`            | string | 64-pixel webpg image of coin icon                                          |
| `exchanges`         | number | number of exchange coin is present at                                      |
| `markets`           | number | number of markets coin is present at                                       |
| `pairs`             | number | number of unique markets coin is present at                                |
| `allTimeHighUSD`    | number | all-time high in USD                                                       |
| `circulatingSupply` | number | number of coins minted, but not locked                                     |
| `totalSupply`       | number | number of coins minted, including locked                                   |
| `maxSupply`         | number | maximum number of coins that can be minted                                 |
| `rate`              | number | price of coin in requested currency                                        |
| `volume`            | number | reported trading volume of the coin in last 24 hours in requested currency |
| `cap`               | number | coin's market cap in requested currency                                    |
| `liquidity`         | number | ±2% orderbook depth                                                        |
| `totalCap`          | number | coin's hypothetical total capitalization at the moment                     |
| `delta.hour`        | number | rate of change in the last hour                                            |
| `delta.day`         | number | rate of change in the last 24 hours                                        |
| `delta.week`        | number | rate of change in the last 7 days                                          |
| `delta.month`       | number | rate of change in the last 30 days                                         |
| `delta.quarter`     | number | rate of change in the last 90 days                                         |
| `delta.year`        | number | rate of change in the last 365 days                                        |

## `/coins/contract`

Get all information about a single coin at latest moment in time, based on its platform identifier and contract address.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/contract' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","platform":"ETH","address":"0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2","meta":true}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/coins/contract"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({
    currency: "USD",
    platform: 'ETH',
    address: '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2',
    meta: true,
  }),
});
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/coins/contract")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"USD\",\n\t\"platform\": \"ETH\",\n\t\"address\": \"0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2\",\n\t\"meta\": true\n}")
  .asString();
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"USD\",\n\t\"platform\": \"ETH\",\n\t\"address\": \"0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2\",\n\t\"meta\": true\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/coins/contract")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/coins/contract"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "USD",
        "platform": "ETH",
        "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
	"meta": true
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/coins/contract");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""USD""," + "\n" +
@"      ""platform"": ""ETH""," + "\n" +,
@"      ""address"": ""0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2""," + "\n" +,
@"	""meta"": true" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/coins/contract"

payload = json.dumps({
  "currency": "USD",
  "platform": "ETH",
  "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
  "meta": True
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'USD', 'platform' => 'ETH', 'address': '0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2', 'meta' => true));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/coins/contract', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/coins/contract")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "USD",
  "platform": "ETH",
  "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
  "meta": true
})

response = https.request(request)
puts response.read_body
```

> Let's see all of current data on ETH, in USD currency:

```json
{
  "code": "ETH",
  "name": "Ethereum",
  "symbol": "Ξ",
  "rank": 2,
  "age": 2411,
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
  "cap": 205915246068,
  "liquidity": 1322914752,
  "delta": {
    "hour": 1.008,
    "day": 1.0808,
    "week": 1.2793,
    "month": 1.4754,
    "quarter": 0.4804,
    "year": 0.7455
  }
}
```

### Request

| key        | type    | description                             |
| ---------- | ------- | --------------------------------------- |
| `currency` | string  | any valid coin or fiat code             |
| `platform` | string  | platform code                           |
| `address`  | string  | contract address                        |
| `meta`     | boolean | to include full coin information or not |

### Response

| key                 | type   | description                                                                |
| ------------------- | ------ | -------------------------------------------------------------------------- |
| `code`              | string | coin's code                                                                |
| `name`              | string | coin's name                                                                |
| `symbol`            | string | coin's symbol                                                              |
| `rank`              | number | coin's rank                                                                |
| `age`               | number | coin's age in days                                                         |
| `color`             | string | hexadecimal color code (`#282a2a`)                                         |
| `png32`             | string | 32-pixel png image of coin icon                                            |
| `png64`             | string | 64-pixel png image of coin icon                                            |
| `webp32`            | string | 32-pixel webp image of coin icon                                           |
| `webp64`            | string | 64-pixel webpg image of coin icon                                          |
| `exchanges`         | number | number of exchange coin is present at                                      |
| `markets`           | number | number of markets coin is present at                                       |
| `pairs`             | number | number of unique markets coin is present at                                |
| `allTimeHighUSD`    | number | all-time high in USD                                                       |
| `circulatingSupply` | number | number of coins minted, but not locked                                     |
| `totalSupply`       | number | number of coins minted, including locked                                   |
| `maxSupply`         | number | maximum number of coins that can be minted                                 |
| `rate`              | number | price of coin in requested currency                                        |
| `volume`            | number | reported trading volume of the coin in last 24 hours in requested currency |
| `cap`               | number | coin's market cap in requested currency                                    |
| `liquidity`         | number | ±2% orderbook depth                                                        |
| `totalCap`          | number | coin's hypothetical total capitalization at the moment                     |
| `delta.hour`        | number | rate of change in the last hour                                            |
| `delta.day`         | number | rate of change in the last 24 hours                                        |
| `delta.week`        | number | rate of change in the last 7 days                                          |
| `delta.month`       | number | rate of change in the last 30 days                                         |
| `delta.quarter`     | number | rate of change in the last 90 days                                         |
| `delta.year`        | number | rate of change in the last 365 days                                        |


## `/coins/single/history`

Historical values for coin.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/single/history' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","code":"BTC","start":1617035100000,"end":1617035400000,"meta":true}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/coins/single/history"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({
    currency: "USD",
    code: "BTC",
    start: 1617035100000,
    end: 1617035400000,
    meta: true,
  }),
});
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/coins/single/history")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"USD\",\n\t\"code\": \"BTC\",\n\t\"start\": 1617035100000,\n\t\"end\": 1617035400000,\n    \"meta\": true\n}")
  .asString();
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"USD\",\n\t\"code\": \"BTC\",\n\t\"start\": 1617035100000,\n\t\"end\": 1617035400000,\n    \"meta\": true\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/coins/single/history")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/coins/single/history"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "USD",
	"code": "BTC",
	"start": 1617035100000,
	"end": 1617035400000,
    "meta": true
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/coins/single/history");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""USD""," + "\n" +
@"	""code"": ""BTC""," + "\n" +
@"	""start"": 1617035100000," + "\n" +
@"	""end"": 1617035400000," + "\n" +
@"    ""meta"": true" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/coins/single/history"

payload = json.dumps({
  "currency": "USD",
  "code": "BTC",
  "start": 1617035100000,
  "end": 1617035400000,
  "meta": True
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'USD', 'code' => 'BTC', 'start' => 1617035100000, 'end' => 1617035400000, 'meta' => true));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/coins/single/history', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/coins/single/history")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "USD",
  "code": "BTC",
  "start": 1617035100000,
  "end": 1617035400000,
  "meta": true
})

response = https.request(request)
puts response.read_body
```

> How is BTC trending over a period of time:

```json
{
  "code": "BTC",
  "name": "Bitcoin",
  "symbol": "₿",
  "rank": 1,
  "age: 4810,
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

| key        | type    | description                                           |
| ---------- | ------- | ----------------------------------------------------- |
| `currency` | string  | any valid coin or fiat code                           |
| `code`     | string  | coin code                                             |
| `start`    | number  | UNIX timestamp in milliseconds of time interval start |
| `end`      | number  | UNIX timestamp in milliseconds of time interval end   |
| `meta`     | boolean | to include full coin information or not               |

### Response

| key                 | type   | description                                 |
| ------------------- | ------ | ------------------------------------------- |
| `code`              | string | coin's own code                             |
| `name`              | string | coin's name                                 |
| `symbol`            | string | coin's symbol                               |
| `rank`              | number | coin's rank                                 |
| `age`               | number | coin's age in days                          |
| `color`             | string | hexadecimal color code (`#282a2a`)          |
| `png32`             | string | 32-pixel png image of coin icon             |
| `png64`             | string | 64-pixel png image of coin icon             |
| `webp32`            | string | 32-pixel webp image of coin icon            |
| `webp64`            | string | 64-pixel webpg image of coin icon           |
| `exchanges`         | number | number of exchange coin is present at       |
| `markets`           | number | number of markets coin is present at        |
| `pairs`             | number | number of unique markets coin is present at |
| `allTimeHighUSD`    | number | all-time high in USD                        |
| `circulatingSupply` | number | number of coins minted, but not locked      |
| `totalSupply`       | number | number of coins minted, including locked    |
| `maxSupply`         | number | maximum number of coins that can be minted  |
| `history`           | array  | list of `date`, `rate`, `volume` and `cap`  |

## `/coins/list`

Assorted information for a list of coins.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/list' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","sort":"rank","order":"ascending","offset":0,"limit":2,"meta":false}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/coins/list"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({
    currency: "USD",
    sort: "rank",
    order: "ascending",
    offset: 0,
    limit: 2,
    meta: false,
  }),
});
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/coins/list")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"USD\",\n\t\"sort\": \"rank\",\n\t\"order\": \"ascending\",\n\t\"offset\": 0,\n\t\"limit\": 2,\n\t\"meta\": false\n}")
  .asString();
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"USD\",\n\t\"sort\": \"rank\",\n\t\"order\": \"ascending\",\n\t\"offset\": 0,\n\t\"limit\": 2,\n\t\"meta\": false\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/coins/list")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/coins/list"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "USD",
	"sort": "rank",
	"order": "ascending",
	"offset": 0,
	"limit": 2,
	"meta": false
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/coins/list");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""USD""," + "\n" +
@"	""sort"": ""rank""," + "\n" +
@"	""order"": ""ascending""," + "\n" +
@"	""offset"": 0," + "\n" +
@"	""limit"": 2," + "\n" +
@"	""meta"": false" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/coins/list"

payload = json.dumps({
  "currency": "USD",
  "sort": "rank",
  "order": "ascending",
  "offset": 0,
  "limit": 2,
  "meta": False
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'USD', 'sort' => 'rank', 'order' => 'ascending', 'offset' => 0, 'limit' => 2,'meta' => false));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/coins/list', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/coins/list")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "USD",
  "sort": "rank",
  "order": "ascending",
  "offset": 0,
  "limit": 2,
  "meta": false
})

response = https.request(request)
puts response.read_body
```

> Let's see top two coins by rank, just frequently-changing data, please:

```json
[
  {
    "code": "BTC",
    "rate": 59075.58195922644,
    "volume": 23100393182,
    "cap": 1102979514307,
    "delta": {
      "hour": 1.008,
      "day": 1.0808,
      "week": 1.2793,
      "month": 1.4754,
      "quarter": 0.4804,
      "year": 0.7455
    }
  },
  {
    "code": "ETH",
    "rate": 1933.6392223621567,
    "volume": 12686119704,
    "cap": 222928063223,
    "delta": {
      "hour": 1.0015,
      "day": 1.0386,
      "week": 1.0822,
      "month": 1.158,
      "quarter": 0.5436,
      "year": 0.7004
    }
  }
]
```

### Request

| key        | type    | description                                                         |
| ---------- | ------- | ------------------------------------------------------------------- |
| `currency` | string  | any valid coin or fiat code                                         |
| `sort`     | string  | sorting parameter, `rank`, `price`, `volume`, `code`, `name`, `age` |
| `order`    | string  | sorting order, `ascending` or `descending`                          |
| `offset`   | number  | offset of the list, default `0`                                     |
| `limit`    | number  | limit of the list, default `10`, maximum `100`                      |
| `meta`     | boolean | to include full coin information or not                             |

### Response

| key                 | type   | description                                 |
| ------------------- | ------ | ------------------------------------------- |
| `name`              | string | coin's name                                 |
| `symbol`            | string | coin's symbol                               |
| `rank`              | rank   | coin's rank                                 |
| `age`               | number | coin's age in days                          |
| `color`             | string | hexadecimal color code (`#282a2a`)          |
| `png32`             | string | 32-pixel png image of coin icon             |
| `png64`             | string | 64-pixel png image of coin icon             |
| `webp32`            | string | 32-pixel webp image of coin icon            |
| `webp64`            | string | 64-pixel webpg image of coin icon           |
| `exchanges`         | number | number of exchange coin is present at       |
| `markets`           | number | number of markets coin is present at        |
| `pairs`             | number | number of unique markets coin is present at |
| `allTimeHighUSD`    | number | all-time high in USD                        |
| `circulatingSupply` | number | number of coins minted, but not locked      |
| `totalSupply`       | number | number of coins minted, including locked    |
| `maxSupply`         | number | maximum number of coins that can be minted  |
| `code`              | string | coin's code                                 |
| `rate`              | number | coin rate in the specified currency         |
| `volume`            | number | 24-hour volume of coin                      |
| `cap`               | number | market cap of coin                          |
| `delta.hour`        | number | rate of change in the last hour             |
| `delta.day`         | number | rate of change in the last 24 hours         |
| `delta.week`        | number | rate of change in the last 7 days           |
| `delta.month`       | number | rate of change in the last 30 days          |
| `delta.quarter`     | number | rate of change in the last 90 days          |
| `delta.year`        | number | rate of change in the last 365 days         |


## `/coins/map`

Assorted information for a custom map of coins.

```shell
curl -X POST 'https://api.livecoinwatch.com/coins/map' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"codes":["ETH","GRIN","BTC"],"currency":"USD","sort":"rank","order":"ascending","offset":0,"limit":2,"meta":false}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/coins/map"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({
    codes: ["ETH", "BTC","GRIN"],
    currency: "USD",
    sort: "rank",
    order: "ascending",
    offset: 0,
    limit: 0,
    meta: false,
  }),
});
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/coins/map")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"codes\": [\"ETH\",\"BTC\",\"GRIN\"],\n\t\"currency\": \"USD\",\n\t\"sort\": \"rank\",\n\t\"order\": \"ascending\",\n\t\"offset\": 0,\n\t\"limit\": 0,\n\t\"meta\": false\n}")
  .asString();
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"codes\": [\"ETH\",\"BTC\",\"GRIN\"],\n\t\"currency\": \"USD\",\n\t\"sort\": \"rank\",\n\t\"order\": \"ascending\",\n\t\"offset\": 0,\n\t\"limit\": 0,\n\t\"meta\": false\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/coins/map")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/coins/map"
  method := "POST"

  payload := strings.NewReader(`{
        "codes": ["ETH","BTC","GRIN"],
	"currency": "USD",
	"sort": "rank",
	"order": "ascending",
	"offset": 0,
	"limit": 0,
	"meta": false
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/coins/map");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"      ""codes"": [""ETH"",""BTC"",""GRIN""]," + "\n" +
@"	""currency"": ""USD""," + "\n" +
@"	""sort"": ""rank""," + "\n" +
@"	""order"": ""ascending""," + "\n" +
@"	""offset"": 0," + "\n" +
@"	""limit"": 0," + "\n" +
@"	""meta"": false" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/coins/map"

payload = json.dumps({
  "codes": ["ETH","BTC","GRIN"],
  "currency": "USD",
  "sort": "rank",
  "order": "ascending",
  "offset": 0,
  "limit": 0,
  "meta": False
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('codes' => array('ETH','BTC','GRIN'), 'currency' => 'USD', 'sort' => 'rank', 'order' => 'ascending', 'offset' => 0, 'limit' => 0,'meta' => false));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/coins/map', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/coins/map")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "codes": ["ETH", "BTC","GRIN"],
  "currency": "USD",
  "sort": "rank",
  "order": "ascending",
  "offset": 0,
  "limit": 0,
  "meta": false
})

response = https.request(request)
puts response.read_body
```

> This should give us 3 coins we specifically requested with their codes.

<aside class="notice">
  Note that the `limit=0` will default your page limit to the size of `codes` specified.
</aside>

```json
[
  {
    "code": "BTC",
    "rate": 24033.24173657366,
    "volume": 14151561000,
    "cap": 459414930787,
    "delta": {
      "hour": 0.9975,
      "day": 1.0445,
      "week": 1.0454,
      "month": 1.106,
      "quarter": 0.7655,
      "year": 0.5399
    }
  },
  {
    "code": "ETH",
    "rate": 1771.4633449389692,
    "volume": 9351819221,
    "cap": 215903855069,
    "delta": {
      "hour": 1.0011,
      "day": 1.0503,
      "week": 1.0769,
      "month": 1.4474,
      "quarter": 0.7453,
      "year": 0.5691
    }
  },
  {
    "code": "GRIN",
    "rate": 0.07354315748650457,
    "volume": 998880,
    "cap": 4625806,
    "delta": {
      "hour": 0.9983,
      "day": 1.0189,
      "week": 1.1734,
      "month": 1.1519,
      "quarter": 0.7298,
      "year": 0.214
    }
  }
]
```

### Request

| key        | type    | description                                                         |
| ---------- | ------- | ------------------------------------------------------------------- |
| `codes`    | array   | array any valid coin code strings                                   |
| `currency` | string  | any valid coin or fiat code                                         |
| `sort`     | string  | sorting parameter, `rank`, `price`, `volume`, `code`, `name`, `age` |
| `order`    | string  | sorting order, `ascending` or `descending`                          |
| `offset`   | number  | offset of the list, default `0`                                     |
| `limit`    | number  | limit of the list, default `10`, maximum `100`                      |
| `meta`     | boolean | to include full coin information or not                             |

### Response

| key                 | type   | description                                 |
| ------------------- | ------ | ------------------------------------------- |
| `name`              | string | coin's name                                 |
| `symbol`            | string | coin's symbol                               |
| `rank`              | rank   | coin's rank                                 |
| `age`               | number | coin's age in days                          |
| `color`             | string | hexadecimal color code (`#282a2a`)          |
| `png32`             | string | 32-pixel png image of coin icon             |
| `png64`             | string | 64-pixel png image of coin icon             |
| `webp32`            | string | 32-pixel webp image of coin icon            |
| `webp64`            | string | 64-pixel webpg image of coin icon           |
| `exchanges`         | number | number of exchange coin is present at       |
| `markets`           | number | number of markets coin is present at        |
| `pairs`             | number | number of unique markets coin is present at |
| `allTimeHighUSD`    | number | all-time high in USD                        |
| `circulatingSupply` | number | number of coins minted, but not locked      |
| `totalSupply`       | number | number of coins minted, including locked    |
| `maxSupply`         | number | maximum number of coins that can be minted  |
| `code`              | string | coin's code                                 |
| `rate`              | number | coin rate in the specified currency         |
| `volume`            | number | 24-hour volume of coin                      |
| `cap`               | number | market cap of coin                          |
| `delta.hour`        | number | rate of change in the last hour             |
| `delta.day`         | number | rate of change in the last 24 hours         |
| `delta.week`        | number | rate of change in the last 7 days           |
| `delta.month`       | number | rate of change in the last 30 days          |
| `delta.quarter`     | number | rate of change in the last 90 days          |
| `delta.year`        | number | rate of change in the last 365 days         |

## `/fiats/all`

List of all the fiats.

```shell
curl -X POST 'https://api.livecoinwatch.com/fiats/all' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/fiats/all"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
});
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/fiats/all")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/fiats/all")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .asString();
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/fiats/all"
  method := "POST"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/fiats/all"

payload={}
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/fiats/all");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
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
$fp = fopen('https://api.livecoinwatch.com/fiats/all', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/fiats/all")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"

response = https.request(request)
puts response.read_body
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

| key         | type   | description                  |
| ----------- | ------ | ---------------------------- |
| `code`      | string | fiat ISO code                |
| `countries` | array  | ISO country code list        |
| `flag`      | string | ISO country code of the flag |
| `name`      | string | fiat name                    |
| `symbol`    | string | fiat symbol                  |


## `/platforms/all`

List of all the coin platforms.

```shell
curl -X POST 'https://api.livecoinwatch.com/platforms/all' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/platforms/all"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
});
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/platforms/all")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/platforms/all")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .asString();
```

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/platforms/all"
  method := "POST"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/platforms/all"

payload={}
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/platforms/all");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
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
$fp = fopen('https://api.livecoinwatch.com/platforms/all', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/platforms/all")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"

response = https.request(request)
puts response.read_body
```

> Array of all the supported platforms:

```json
[
  {
    "code": "BSC",
    "name": "BNB Chain"
  },
  {
    "code": "ETH",
    "name": "Ethereum"
  },
  ...
]
```

### Request

Accepts no request parameters.

### Response

An array of following:

| key         | type   | description                          |
| ----------- | ------ | ------------------------------------ |
| `code`      | string | platform code                        |
| `name`      | string | platform name                        |


## `/exchanges/single`

Assorted exchange information.

```shell
curl -X POST 'https://api.livecoinwatch.com/exchanges/single' \
  -H 'content-type: application/json' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"ETH","code":"gemini","meta":true}'
```

```javascript
await fetch(new Request("https://api.livecoinwatch.com/exchanges/single"), {
  method: "POST",
  headers: new Headers({
    "content-type": "application/json",
    "x-api-key": "<YOUR_API_KEY>",
  }),
  body: JSON.stringify({
    currency: "ETH",
    code: "gemini",
    meta: true,
  }),
});
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/exchanges/single"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "ETH",
	"code": "gemini",
	"meta": true
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"ETH\",\n\t\"code\": \"gemini\",\n\t\"meta\": true\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/exchanges/single")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/exchanges/single")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"ETH\",\n\t\"code\": \"gemini\",\n\t\"meta\": true\n}")
  .asString();
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/exchanges/single");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""ETH""," + "\n" +
@"	""code"": ""gemini""," + "\n" +
@"	""meta"": true" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```


```python
import requests
import json

url = "https://api.livecoinwatch.com/exchanges/single"

payload = json.dumps({
  "currency": "ETH",
  "code": "gemini",
  "meta": True
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'ETH', 'code' => 'gemini', 'meta' => true));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/exchanges/single', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/exchanges/single")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "ETH",
  "code": "gemini",
  "meta": true
})

response = https.request(request)
puts response.read_body
```

> Should get us all the information we have on Gemini exchange:

```json
{
  "name": "Gemini",
  "png64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/gemini.png",
  "png128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/gemini.png",
  "webp64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/gemini.webp",
  "webp128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/gemini.webp",
  "centralized": true,
  "usCompliant": true,
  "code": "gemini",
  "markets": 43,
  "volume": 115473.97264617922,
  "bidTotal": 10968.751251210175,
  "askTotal": 12183.016333351212,
  "depth": 23151.76758456139,
  "visitors": 31738,
  "volumePerVisitor": 3.638350641066835
}
```

### Request

| key        | type    | description                                 |
| ---------- | ------- | ------------------------------------------- |
| `currency` | string  | any valid coin or fiat code                 |
| `code`     | string  | exchange code                               |
| `meta`     | boolean | to include full exchange information or not |

### Response

| key                | type    | description                                       |
| ------------------ | ------- | ------------------------------------------------- |
| `name`             | string  | exchange name                                     |
| `png64`            | string  | 64-pixel png image of exchange icon               |
| `png128`           | string  | 128-pixel png image of exchange icon              |
| `webp64`           | string  | 64-pixel webp image of exchange icon              |
| `webp128`          | string  | 128-pixel webpg image of exchange icon            |
| `centralized`      | boolean | is the exchange centralized or decentralized      |
| `usCompliant`      | boolean | is the exchange compliant in the USA              |
| `code`             | string  | exchange code                                     |
| `markets`          | number  | count of currently active markets on the exchange |
| `volume`           | number  | 24-hour volume in specified currency              |
| `bidTotal`         | number  | 2% orderbook value bids                           |
| `askTotal`         | number  | 2% orderbook value asks                           |
| `depth`            | number  | 2% orderbook total depth                          |
| `visitors`         | number  | number of daily visitors, estimate                |
| `volumePerVisitor` | number  | daily volume per daily visitor                    |

## `/exchanges/list`

Assorted information on list of exchanges.

```shell
curl -X POST 'https://api.livecoinwatch.com/exchanges/list' \
  -H 'x-api-key: <YOUR_API_KEY>' \
  -d '{"currency":"USD","sort":"visitors","order":"descending","offset":0,"limit":1,"meta":true}'
```

```javascript
await fetch(new Request('https://api.livecoinwatch.com/exchanges/list'), {
  method: 'POST',
  headers: new Headers({
    'content-type': 'application/json',
    'x-api-key': '<YOUR_API_KEY>'
  }),
  body: JSON.stringify({
    currency: 'USD',
    sort: 'visitors',
    order: 'descending',
    offset: 0,
    limit: 1
    meta: true
  })
})
```

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

let parameters = "{\n\t\"currency\": \"USD\",\n\t\"sort\": \"visitors\",\n\t\"order\": \"descending\",\n\t\"offset\": 0,\n\t\"limit\": 1,\n\t\"meta\": true\n}"
let postData = parameters.data(using: .utf8)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com/exchanges/list")!,timeoutInterval: Double.infinity)
request.addValue("application/json", forHTTPHeaderField: "content-type")
request.addValue("<YOUR_API_KEY>", forHTTPHeaderField: "x-api-key")

request.httpMethod = "POST"
request.httpBody = postData

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    semaphore.signal()
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/exchanges/list")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .body("{\n\t\"currency\": \"USD\",\n\t\"sort\": \"visitors\",\n\t\"order\": \"descending\",\n\t\"offset\": 0,\n\t\"limit\": 1,\n\t\"meta\": true\n}")
  .asString();
```

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com/exchanges/list"
  method := "POST"

  payload := strings.NewReader(`{
	"currency": "USD",
	"sort": "visitors",
	"order": "descending",
	"offset": 0,
	"limit": 1,
	"meta": true
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("content-type", "application/json")
  req.Header.Add("x-api-key", "<YOUR_API_KEY>")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/exchanges/list");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
request.AddHeader("x-api-key", "<YOUR_API_KEY>");
var body = @"{" + "\n" +
@"	""currency"": ""USD""," + "\n" +
@"	""sort"": ""visitors""," + "\n" +
@"	""order"": ""descending""," + "\n" +
@"	""offset"": 0," + "\n" +
@"	""limit"": 1," + "\n" +
@"	""meta"": true" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```python
import requests
import json

url = "https://api.livecoinwatch.com/exchanges/list"

payload = json.dumps({
  "currency": "USD",
  "sort": "visitors",
  "order": "descending",
  "offset": 0,
  "limit": 1,
  "meta": True
})
headers = {
  'content-type': 'application/json',
  'x-api-key': '<YOUR_API_KEY>'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```php
$data = json_encode(array('currency' => 'USD', 'sort' => 'visitors', 'order' => 'descending', 'offset' => 0, 'limit' => 1, 'meta' => true));
$context_options = array (
    'http' => array (
        'method' => 'POST',
        'header' => "Content-type: application/json\r\n"
            . "x-api-key: <YOUR_API_KEY>" . "\r\n",
        'content' => $data
    )
);
$context = stream_context_create($context_options);
$fp = fopen('https://api.livecoinwatch.com/exchanges/list', 'r', false, $context);
print_r(stream_get_contents($fp));
```

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com/exchanges/list")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"
request["x-api-key"] = "<YOUR_API_KEY>"
request.body = JSON.dump({
  "currency": "USD",
  "sort": "visitors",
  "order": "descending",
  "offset": 0,
  "limit": 1,
  "meta": true
})

response = https.request(request)
puts response.read_body
```

> Top one exchange by number of visitors:

```json
[
  {
    "name": "Binance",
    "png64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/binance.png",
    "png128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/binance.png",
    "webp64": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/64/binance.webp",
    "webp128": "https://lcw.nyc3.cdn.digitaloceanspaces.com/development/exchanges/128/binance.webp",
    "centralized": true,
    "usCompliant": true,
    "code": "binance",
    "markets": 935,
    "volume": 27523372418,
    "bidTotal": 225078060.0687528,
    "askTotal": 240112799.048314,
    "depth": 465190859.1170668,
    "visitors": 779440,
    "volumePerVisitor": 35311.72690393103
  }
]
```

### Request

| key        | type    | description                                              |
| ---------- | ------- | -------------------------------------------------------- |
| `currency` | string  | any valid coin or fiat code                              |
| `sort`     | string  | sorting parameter, `volume`, `liquidity`, `code`, `name` |
| `order`    | string  | sorting order, `ascending` or `descending`               |
| `offset`   | number  | offset of the list, default `0`                          |
| `limit`    | number  | limit of the list, default `50`, maximum `100`           |
| `meta`     | boolean | to include full exchange information or not              |

### Response

Returns array of objects containing:

| key                | type    | description                                       |
| ------------------ | ------- | ------------------------------------------------- |
| `name`             | string  | exchange name                                     |
| `png64`            | string  | 64-pixel png image of exchange icon               |
| `png128`           | string  | 128-pixel png image of exchange icon              |
| `webp64`           | string  | 64-pixel webp image of exchange icon              |
| `webp128`          | string  | 128-pixel webpg image of exchange icon            |
| `centralized`      | boolean | is the exchange centralized or decentralized      |
| `usCompliant`      | boolean | is the exchange compliant in the USA              |
| `code`             | string  | exchange code                                     |
| `markets`          | number  | count of currently active markets on the exchange |
| `volume`           | number  | 24-hour volume in specified currency              |
| `bidTotal`         | number  | 2% orderbook value bids                           |
| `askTotal`         | number  | 2% orderbook value asks                           |
| `depth`            | number  | 2% orderbook total depth                          |
| `visitors`         | number  | number of daily visitors, estimate                |
| `volumePerVisitor` | number  | daily volume per daily visitor                    |

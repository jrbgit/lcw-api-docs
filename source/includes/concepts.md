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

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/status")
  .header("content-type", "application/json")
  .asString();
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/status");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
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

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/credits")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .asString();
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

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/status")
  .header("content-type", "application/json")
  .asString();
```

```csharp
var client = new RestClient("https://api.livecoinwatch.com/status");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
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

## There Is Only One **Delta**

There is only one way rate of change is represented, and that's a floating-point number ranging from `0` to `2`, `1` meaning no change has happened.

If you need percentages, it is easy to calculate with `(delta - `) * 100`.

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

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com/credits")
  .header("content-type", "application/json")
  .header("x-api-key", "<YOUR_API_KEY>")
  .asString();
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

> Don't forget to replace `<YOUR_API_KEY>` with one you've got. Return response should be:

```json
{
  "dailyCreditsRemaining": 4321,
  "dailyCreditsLimit": 100000
}
```

Let's call it *credits*, and you can read about them [in detail](#limits), but summarized - they map directly to your requests 1-to-1.

You can always easily check your credits status at `/credits` end-point, as well as on your Live Coin Watch [profile page](https://www.livecoinwatch.com/profile).

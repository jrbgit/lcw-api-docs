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

## Python

```python 
import requests
import json

url = "https://api.livecoinwatch.com"

payload={}
headers = {
  'content-type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

All the examples are written using [Python Requests](https://docs.python-requests.org/en/latest/).

[Install the library](https://docs.python-requests.org/en/latest/user/install/#install) and import it along with the json library. 

Note that you don't have to install the json library, only import it.


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

## C#

```csharp
var client = new RestClient("https://api.livecoinwatch.com");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("content-type", "application/json");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

All the examples are written using the [RestSharp](https://restsharp.dev/).

Install the package and add it to your code. Everything is explained in their [documentation](https://restsharp.dev/intro.html).

## Ruby

```ruby
require "uri"
require "json"
require "net/http"

url = URI("https://api.livecoinwatch.com")

https = Net::HTTP.new(url.host, url.port)
https.use_ssl = true

request = Net::HTTP::Post.new(url)
request["content-type"] = "application/json"

response = https.request(request)
puts response.read_body
```

All the examples use [Net::HTTP](https://ruby-doc.org/stdlib-2.7.0/libdoc/net/http/rdoc/Net/HTTP.html). 
Examples work without installing any package! Just change the `<YOUR_API_KEY>` to your key, and that's it!. Don't forget to require "json" and "uri".

## Go

```go
package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.livecoinwatch.com"
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

All the examples are written using net/http. 
Everything is explained in their [documentation](https://pkg.go.dev/net/http)!.
Just copy and paste and you are ready to Go!. Remember to change `<YOUR_API_KEY>` to your API key.

## Swift

```swift
import Foundation
#if canImport(FoundationNetworking)
import FoundationNetworking
#endif

var semaphore = DispatchSemaphore (value: 0)

var request = URLRequest(url: URL(string: "https://api.livecoinwatch.com")!,timeoutInterval: Double.infinity)
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

All the examples use [URLRequest](https://developer.apple.com/documentation/foundation/urlrequest) and [URLSession](https://developer.apple.com/documentation/foundation/urlsession). 
Examples work without installing any package! Just change the `<YOUR_API_KEY>` to your key, and that's it!.

## Java

```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.post("https://api.livecoinwatch.com")
  .header("content-type", "application/json")
  .asString();
```

The examples are written using [Java Unirest](https://kong.github.io/unirest-java/).
You may want to follow this guide for [an example](https://www.baeldung.com/unirest).
You can also read the [documentation](https://kong.github.io/unirest-java/).
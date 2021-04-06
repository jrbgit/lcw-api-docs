# Errors

> Example end-point with JSON error information:

```json
{
  "error": {
    "code": 418,
    "status": "I'm a teapot.",
    "description": "Yes, a teapot"
  }
}
```

Errors follow [There Is Only One Format](#there-is-only-one-format) as well.

<aside class="notice">
This doesn't mean HTTP end-points won't have the same status code assigned as well. We recommend you use error information from the JSON response though.
</aside>

code | status | description
--- | --- | ---
400 | Bad Request | Your request is invalid.
401 | Unauthorized | Your API key is wrong.
403 | Forbidden | The resource requested is hidden for administrators only.
404 | Not Found | The specified resource could not be found.
405 | Method Not Allowed | You tried to access a resource with an invalid method.
406 | Not Acceptable | You requested a format that isn't json.
410 | Gone | The resource requested has been removed from our servers.
418 | I'm a teapot. |  Yes, a teapot.
429 | Too Many Requests | You're requesting too many resources! Slow down!
500 | Internal Server Error | We had a problem with our server. Try again later.
503 | Service Unavailable | We're temporarily offline for maintenance. Please try again later.

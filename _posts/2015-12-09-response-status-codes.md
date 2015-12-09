---
title: 'Response status codes'

layout: nil
---

### Success

Successes differ from errors in that their body may not be a simple response object with a code and a message. The headers however are consistent across all calls:

* `GET`, `PUT`, `DELETE` returns `200 OK` on success,
* `POST ` returns 201 on success,

When [retrieving stuff](#get-stuff) for example:

```Status: 200 OK```
```{
    {
        id: thing_1,
        name: 'My first thing'
    },
    {
        id: thing_2,
        name: 'My second thing'
    }
}```

### Error

Error responses are simply returning [standard HTTP error codes](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) along with some additional information:

* The body includes an object describing both the code and message (for debugging and/or display purposes),

For a call with a bad request, where some input values are missing or a malformed request, for example:

```Status: 400 Bad Request```
```{
    message: 'Malformed Request <Reasons, if available>'
}```

For a call with an invalid authentication token for example:

```Status: 401 Access Denied```
```{
    message: 'Invalid Token'
}```

If an issue that has happened in the middleware/database/backend systems which is irrecoverable, for example:

```Status: 500 Internal Server Error```
```{
    message: 'Something wrong happened in the servers!'
}```


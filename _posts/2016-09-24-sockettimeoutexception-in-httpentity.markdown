---
layout: post
title: "SocketTimeoutException in HttpEntity"
date: 2016-09-24T18:45:26+05:30
author: Swathi Venkatachala
comments: true
tags:
- HttpEntity
- SocketTimeoutException
- Socket
- API
- java
---


Ever ran into a production issue with SocketTimeoutException or Socket Closed error? Well it can be daunting to
find that culprit. If you faced a similar situation while using HttpEntity, I have found a remedy.

Follow the snippet along.



The key point here to note is `httpResponse.getEntity()` returns `HttpEntity` is hooked up with the same
underlying connection. So we have to consume the required repsonse content as `EntityUtils.toString(httpResponse.getEntity())` before the `HttpResponse` is close. Having failed to do that the connection will be reset and throws the
`Socket closed Error`.

Happy Debugging! :)

- Swatz


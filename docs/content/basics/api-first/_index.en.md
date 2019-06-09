---
title: API-first
weight: 10
disableToc: true
---

Once AbterCMS has more than one implementation, it will be absolutely crucial to have a consistent and stable API so that the different implementations remain incompatible, because it should always be possible to switch to a different backend or frontend stack without having to modify anything but a few settings.

Moreover we also want to respect all applications built on top of AbterCMS and ensure that updates don't break any applications built using the API. In this regard, we want to follow in the footsteps of [Go and its compatibility promises](https://golang.org/doc/go1compat), meaning once we reach 1.0, we will only break backwards compatibility if there is absolutely no other way around a security issue. Since AbterCMS will make relatively few security related promises, as most of that is delegated to the implementations, this likely won't ever happen.

AbterCMS API will firstly be a RESTful API which will adhere to all rules defined in [Zalando API Guidelines](https://github.com/zalando/restful-api-guidelines). These particular guidelines were chosen because they are comprehensive and are based on widely-accepted best practices and have some good linters to enforce them.

It is completely possible that eventually other interfaces will be defined, but for all 1.x stable releases the RESTful API will be considered as the reference interface.
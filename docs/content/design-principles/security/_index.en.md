---
title: Security
weight: 20
---

Security can mean a lot of things, but in this day and age everyone needs to do their best to keep their own data, their customers' data and their partners' data safe from anyone who's not explicitly authorized access to that data. Building a secure system is not obvious, nor is it an absolute state of any existing system. We aim to be biased for security, even if it means we have to compromise usability or performance.

This document lists a couple of ways we find generally important, but keep in mind that actual implementations (like [AbterPHP](https://abterphp.abtercms.com/)) may provide even more security features in some cases.

### Incomprehensive list of security features

1. Modern handling of [passwords and secrets]({{< ref "/features/passwords-and-secrets/_index.en.md" >}})
1. [Login throttling]({{< ref "/features/authentication/_index.en.md#login-throttling" >}})
1. [2FA / MFA]({{< ref "/features/authentication/_index.en.md#multi-factor-authentication-2fa-mfa" >}})
1. [SSL-only]({{< ref "/features/ssl-only/_index.en.md" >}})
1. [Private file upload directories]({{< ref "/components/files/entities/_index.en.md#files" >}})
1. [Sane and safe configs]({{< ref "/features/configuration/_index.en.md#sane-and-safe-configs" >}})
1. [Secure HTTP headers]({{< ref "/features/secure-http-headers/_index.en.md" >}})
1. [Flexible authorization options]({{< ref "/features/authorization/_index.en.md" >}})
1. [Hard to guess login, admin and API URLs]({{< ref "/features/configuration/_index.en.md#hard-to-guess-login-admin-and-api-urls" >}})

### OWASP Top 10, etc

Obviously the above list says little about how AbterCMS is supposed to help you defend against [SQL injection](https://www.owasp.org/index.php/Top_10-2017_A1-Injection), [Cross-Site Scripting (XSS)](https://www.owasp.org/index.php/Top_10-2017_A7-Cross-Site_Scripting_(XSS)), [Insecure deserialization](https://www.owasp.org/index.php/Top_10-2017_A8-Insecure_Deserialization) and many other threats. It's mainly because we consider these threats to be something the actual implementations will have different solutions for. Underlying frameworks and language best practices are likely to take care of most of them.

There's one obvious exception to this: [Insufficient Logging and Monitoring](https://www.owasp.org/index.php/Top_10-2017_A10-Insufficient_Logging%26Monitoring). This one is not covered here because it is mostly outside of the scope of AbterCMS. We will however try to provide you with guides how to operate AbterCMS in a handful of environments that affect this topic.

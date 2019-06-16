---
title: Configuration
weight: 50
disableToc: true
---

### Environment variables

AbterCMS acknowledges the points [The Twelve-factor App Manifest](https://12factor.net/) makes about [storing configs in the environment](https://12factor.net/config) and aims to keep any important configuration easy to override in environment variables.

That said, it is perfectly okay and reasonable to provide a way for providing sane defaults in any form that is considered standard for a given implementation.

### Sane and safe configs

No matter how secure a system can be, it must always be configured properly. It must be ensured that salts and peppers, private and public keys are unique and that cryptography is setup so that it makes a good compromise between speed and safety according to the needs and resources available.

AbterCMS helps you in two ways with this:

1. On startup it must be checked that no "default" value is leaked into your configuration.

2. On request it can generate reasonable defaults for you. This means that backend solutions must provide a (command line) tool which can display sane defaults for you. Optionally it may also be able to replace the current 

### Hard to guess login, admin and API URLs

The router of AbterCMS is also prepared to use custom login, admin and API base URLs. While this is certainly not something to make your system safe out of the box, it is a nice little additional layer of security.
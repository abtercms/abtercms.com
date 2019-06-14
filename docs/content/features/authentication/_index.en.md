---
title: Authentication
weight: 20
disableToc: true
---

### Authentication basics

When users try to get access to the admin interface, they will need to go through a login process, sending both a username (or email address) and a password to the server. Similarly, when an API client tries to retrieve a token, it will need to send a client ID and a client secret to the server.

On the surface our login mechanism is hardly different from what most users are used to, but as explained in the [Passwords and Secrets section]({{% relref "features/passwords-and-secrets/_index.md" %}}), the servers should never receive your raw passwords and secrets, instead it should already receive a salted and hashed value.

### Login throttling

As a further brute force attack counter measurement, login attempts both for users and API clients are throttled. This means that after a number of failed attempts to authenticate as a user or API client will result in a temporary ban from further attempts for the user or the API client. This will also happen if the attacker tries to use multiple IP addresses.

There's also a check for authentication attempts based on the IP which tries to prevent attackers finding users with weak passwords.

### Multi-factor authentication (2FA / MFA)

Although it is not yet implemented, and some of the details are still uncertain, the first stable version of AbterCMS will come with [MFA](https://en.wikipedia.org/wiki/Multi-factor_authentication). It is also almost certain to be enabled by default as it is considered best practise.

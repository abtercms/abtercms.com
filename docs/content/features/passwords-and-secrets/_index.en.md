---
title: Passwords and secrets
weight: 10
disableToc: true
---

{{% notice info %}}
AbterCMS Team is aware of [the problem with passwords](https://medium.com/asecuritysite-when-bob-met-alice/the-problem-with-passwords-b555dbab07f4) and [Zero Knowledge Proof](https://en.wikipedia.org/wiki/Zero-knowledge_proof) has members who consider [Prof Bill Buchanan OBE's post](https://medium.com/asecuritysite-when-bob-met-alice/when-peggy-met-victor-its-goodbye-to-an-old-world-of-hashed-passwords-and-hello-to-zero-knowledge-c94827aa22f4) a great inspiration. We're also aware of [Vault by Hashicorp](https://www.vaultproject.io/), [Argond2](https://en.wikipedia.org/wiki/Argon2) and [Chacha20-Poly1305](https://en.wikipedia.org/wiki/Salsa20#ChaCha_variant). These technologies may be incorporated before the first stable release of AbterCMS, but for the time being we will prefer a more traditional stack.
{{% /notice %}}

As hopefully everybody knows by now, the time of storing raw passwords is long gone. However, there are still billion dollar companies found guilty of this in 2019. (e.g [Google](https://www.bleepingcomputer.com/news/security/google-stored-unhashed-g-suite-passwords-for-over-a-decade/), [Facebook](https://krebsonsecurity.com/2019/03/facebook-stored-hundreds-of-millions-of-user-passwords-in-plain-text-for-years/))

Hashing passwords with checksum algorithms like `md5` or [sha1](https://www.computerworld.com/article/3173616/the-sha1-hash-function-is-now-completely-unsafe.html) is also long gone, but both are still widely used. Many open source systems also base their security on them to this day.

Storing secrets in databases is one thing, but the list of companies that were found guilty in having raw passwords in logs is also staggering. (e.g. [Github](https://www.bleepingcomputer.com/news/security/github-accidentally-recorded-some-plaintext-passwords-in-its-internal-logs/), [Twitter](https://www.bleepingcomputer.com/news/security/twitter-admits-recording-plaintext-passwords-in-internal-logs-just-like-github/))

Telling users to use various character categories is also close to useless in the age of [password guessing tools](https://hackernoon.com/how-artificial-intelligence-can-be-used-for-password-guessing-cf4fd4184a46).

Not all hope is lost though! Here's our solution, heavily and proudly inspired by [Florian Harwoeck's](https://medium.com/@harwoeck) ["Password and Credential Management in 2018"](https://medium.com/@harwoeck/password-and-credential-management-in-2018-56f43669d588).

### Strong passwords and secrets

Secrets and passwords are similar, but secrets are generated automatically and passwords are provided by the user. Passwords may also be generated automatically, but no AbterCMS implementations support this out of the box at the moment.

Secrets are generated with [CSPRNG](https://en.wikipedia.org/wiki/Cryptographically_secure_pseudorandom_number_generator) and passwords are checked with [zxcvbn](https://github.com/dropbox/zxcvbn). Both have implementations for many languages to ensure that these choices do not limit AbterCMS implementations too much. Note also that both password generation and checking should happen on the client side, meaning that the JavaScript implementations should be generally enough.

Since secret generation happens on the client side, all clients must enable displaying the secret generated, and / or copying it to clipboard.

To encourage the use of [password managers](https://medium.com/s/the-firewall/episode4-password-managers-ce5576e96e85), AbterCMS implementations must play well with them.

### Never find raw passwords or secrets during audit

Passwords and secrets must be salted and hashed on the client-side. In theory, any 512-bit hashing algorithm could be used on the frontend, but AbterPHP currently ships with `SHA3-512` and that's also our current recommendation. This means that the raw password never reaches the server, therefore it can not be logged by accident. It also means that the backend is not able to check password rules, that's why those must be enforced on the client side.

To ensure that no default values are used, AbterCMS checks the `frontend salt` when run in a production environment.

### Storing passwords and secrets

To ensure that stored password and secret hashes can not be extracted, the backend spices the received hash with the `backend pepper` and hashes it with a [KDF](https://en.wikipedia.org/wiki/Key_derivation_function), [PBKDF2](https://en.wikipedia.org/wiki/PBKDF2) to be precise. Our current implementations use [bcrypt](https://en.wikipedia.org/wiki/Bcrypt) as that is considered safe and widely available.

Before the derived key is stored however, we also encrypt it using a [Symmetric Encryption](https://en.wikipedia.org/wiki/Symmetric-key_algorithm). Our current implementations use [AES256-GCM](https://medium.com/@harwoeck/password-and-credential-management-in-2018-56f43669d588) as that is also considered safe and widely available.

To ensure that no default values are used, AbterCMS checks the `backend pepper` when run in a production environment.

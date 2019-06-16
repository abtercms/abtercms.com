---
title: UUID primary keys
weight: 60
disableToc: true
---

{{% notice warning %}}
The current database schema of [AbterPHP](https://abterphp.abtercms.com/en/) stores IDs naively in `char(36)` columns. This is purely a temporary, technical workaround and is planned to be changed before the first stable release.
{{% /notice %}}

While the pros and cons of this design decision is certainly make up for a long list, AbterCMS for the time being will default to use UUIDs as primary keys. We also experimented with ULIDs which we consider a very viable and promising alternative, but it's not yet supported by databases and therefore we decided to use UUIDv4 instead.

If you want to learn more about the pros and cons of this design decision, we recommend reading [Tom Harrison's post](https://tomharrisonjr.com/uuid-or-guid-as-primary-keys-be-careful-7b2aa3dcb439)
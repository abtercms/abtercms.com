---
title: Authorization
weight: 30
disableToc: true
---

AbterCMS embraces [Casbin](https://casbin.org/), a language-independent and very flexible authorization library.

It's acknowledged that different problems may require different solutions, but by default AbterCMS aims to provide a flexible framework for authorization by assigning resources to user teams and allowing users to be part of multiple teams.

API clients may shrink their scopes, but may never be authorized to do anything that their owner users are not authorized to do. 

Similarly tokens may also shrink their scopes compared to the API client that requested them, but never extend it.

### Example

The [File Component]({{%relref "components/files/_index.en.md" %}}) allows uploading various files. Each file belongs to a file category. File categories can belong to one or many user groups, which means that if user groups "File uploader" and "Admin" are both assigned to the file categories "General" and "Christmas 2021", than any user who is part of the "File uploader" or "Admin" group may download, change or delete files which belong to categories "General" or "Christmas 2021".
---
title: Entities
weight: 10
disableToc: true
---

There are 5 related entity types you need to familiarize yourself with:

1. Users
2. User languages
5. Admin resources
3. User groups
4. API clients
6. Tokens

### Users

Users are probably self-explanatory entities of any administration system. It's important to note, that not all users are allowed to log into the administration interface therefore it might be reasonable to create user entities for other means too, for example for newsletter subscribers or customers.

**Security note:** A user password is obviously highly sensitive data. As part of our security procedures, the secret itself should never reach the backend server. It must be provided by the user twice, salted and hashed by the client before it's sent.

### User languages

User languages simply define the language used (or preferred) by a user.

### Admin resources

Admin resources are used for describing a resources and type.

A straight forward example of this entity would be an admin resource called "users-read" which could allow read access to the "User Management" part of an admin interface or related API endpoints. If the currently logged in user or API client has this admin resource assigned, it should be possible to list users in the system, but not to create, update or delete them.

### User groups

User groups allow fine grained authorization. A user may belong to multiple user groups and each user group may grant access to various admin resources.

**Note:** There are no immediate plans to provide a mechanism to take access away.

### Tokens

Tokens are used to prove the API server that the API client is authorized to access a resource. Tokens expire with time, but the period a token is valid for can be configured.

### API clients

API clients always belong to users. Client ID and client secret are generated during the creation of the API client. 

**Security note:** Since an API client is potentially able to do anything that its owner is allowed to do, the API client secret is considered as highly sensitive data. As part of our security procedures, the secret itself should never reach the backend server. Instead it must be generated, salted and hashed by the client before it's sent.

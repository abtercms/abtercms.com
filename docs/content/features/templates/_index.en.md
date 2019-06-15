---
title: Templates
weight: 100
disableToc: true
---

All AbterCMS backend implementations must provide a simple templating system that enables rendering various template types as HTML.

### Template formatting

1. Templates `MUST BE` wrapped in double braces and `MUST HAVE` a template type descriptor and an entity descriptor separated by a forward slash.
2. The two opening and closing braces `MUST NOT` include white-spaces.
3. Both the template type descriptor and the entity descriptor `MAY` be preceded or followed by a number of whitespace characters.
4. Both the template type descriptor and the entity descriptor `MUST NOT` be empty.
5. Template type descriptors `MAY` only contain characters from the English alphabet, digits, underscores and dashes.
6. Entity descriptors `MAY` only contain characters from the English alphabet, digits, underscores, dashes and forward slashes.
7. Dashes in descriptors `MUST BE` preceded by and followed by an alphanumeric character.
8. Both template and entity descriptors `SHOULD` only contain lowercase characters and prefer dashes instead of underscores.

**Valid template examples:**

- `{{var/author}}`
- `{{0-1/author}}`
- `{{block/author/name}}`
- `{{vaR-2/autH0R}}`
- `{{    vaR-2  /   autH0R_   / NAME  }}`

**Invalid template examples:**

- `{{ abc  }}` (1.)
- `{{var/author} }` (2.)
- `{{var/}}` (4.)
- `{{/author}}` (4.)
- `{{v@r/author}}` (5.)
- `{{var/@uthor}}` (6.)
- `{{0-/author}}` (7.)
- `{{-0/author}}` (7.)

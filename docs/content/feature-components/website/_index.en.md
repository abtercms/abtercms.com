---
title: Website
weight: 10
disableToc: true
---

## Website Entities

The Website Component is designed to provide utilities for displaying webpages. There are 5 related entity types you need to familiarize yourself with:

1. Pages
2. Page layouts
3. Page categories
4. Blocks
5. Block categories

### Pages

Pages are the base building blocks for creating a new page for your website. They're the only entities in the Website Component that can be rendered alone.

In the simplest case, you can just create a new page with providing just a title and activating it. The system can then generate a web-safe and SEO-friendly URL and your new, empty page could be displayed immediately.

Pages however allow you to do a whole lot more, from providing page specific headers, HTML content, lead, custom layouts, selecting existing layouts and some more.

### Page Layouts

Pages allow you to provide a custom layout, but in most cases pages, or at least some of the pages, will need to look similarly. Layouts allow you to define a formatting and assets that is to be shared among the pages. The layout body is an HTML template and it's also possible to provide various headers that will typically serve as default values for the pages using the layout.

If both the page and its layout define CSS or JS headers, then everything gets imported, but with the layout files being defined first. This means that whatever you import for the page can override rules and code imported by the layout.

### Page Categories

Page categories are primarily used to be able to define page collections.

### Blocks

Blocks provide you with the possibility to split the content of a website into smaller, independent chunks and also to reuse them for multiple pages if needed.

### Block Layouts

Similarly to page layouts, block layouts can help you format your blocks in a reusable manner.


## Templating

All AbterCMS backend implementations must provide a simple templating system that enables rendering various template types as HTML. It must always be possible to register more template types, but here's a list of template types readily available in AbterCMS:

1. Variables
2. Blocks
3. Public files (from the [Files module]({{% relref "feature-components/files/_index.en.md" %}}))


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

### Variable Templates

Variable templates can be used to display certain attributes of the entity being rendered. AbterCMS will do its best to figure out the variable implied by the template provided.

For example the following template could mean a number of things when rendered in a block:

```
This article was written by {{ var/author }}.
```

AbterCMS will try to look for an `author` value in the following order:

1. It will check if the block has a non-empty `author` attribute
2. It will check if the block has a layout that has a non-empty `author` attribute
3. It will check if the block belongs to a page with a non-empty `author` attribute
4. It will check if the block belongs to a page with a layout with a non-empty `author` attribute 

*Note:* Implementations may choose not to execute each step separately, but construct a database query to achieve the above in one step instead.

### Block Templates

Block templates can be used to ensure flexibility and reusability. In theory, blocks can also be nested into each other.

#### Example

Let's say you need to display three similar banners on all the "post" pages that belong to the "blog" category.

Here's what you'll need to ensure:

1. A page category with type "blog" exists
2. A block layout exists that creates decoration for the banners (borders, paddings, margins, background, etc.)
3. 3 blocks exist with the contents of the 3 banners, all using the block layout created above.
4. A page layout exists that decorates the page and includes the 3 blocks.
5. All pages in category type "blog" should be assigned to the new page layout.

### Public Files Templates

AbterCMS has an easy way to display files publicly by file categories. It will generate an unordered list with the files
ready to be downloaded.

```
{{ files/file-category-identifier }}
```

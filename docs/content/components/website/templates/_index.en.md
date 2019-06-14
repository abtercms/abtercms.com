---
title: Templates
weight: 20
disableToc: true
---

*Note:* You can [learn about templates in AbterCMS here]({{%relref "features/templates/_index.en.md" %}}).

The Website Component provides two template types out of the box:

1. Variables
2. Blocks

### Variable Templates

Variable templates can be used to display certain attributes of the entity being rendered. AbterCMS will do its best to figure out the variable implied by the template provided.

For example the following template could mean a number of things when rendered in a block:

    This article was written by {{ var/author }}.

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

    {{ files/file-category-identifier }}

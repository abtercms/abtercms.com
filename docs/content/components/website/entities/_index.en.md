---
title: Entities
weight: 10
disableToc: true
---

There are 5 related entity types you need to familiarize yourself with:

1. Pages
2. Page layouts
3. Page categories
4. Blocks
5. Block layouts

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

---
description: >-
  One of Betterprint's powerful benefits are dynamic Header and Footer. They
  will allow features like multiple-headers per Document, Adding running Texts
  or Numbers into the header and much more.
icon: sheet-plastic
---

# Dynamic Header & Footer

### Basics

Betterprint's dynamic feature is based on paginate-source and paginate-target elements. All contents of the paginate-source element will be displayed within the appropriate paginate-target element. In order to link source and target with each other, we need to set the data-key attribute with any custom key:

```
<paginate-source data-key="MYCUSTOMKEY"></paginate-source>
```

### Running content

Source elements will allow to add dynamic values into your header. Each target element will always display only the previous source content, which allows defining a source multiple times in order to display different content on each page. Let's make an example:

```html
<!-- Set the footer content -->
<paginate-source data-key="footer">
    <h1><paginate-target data-key="chapter"></paginate-target></h1>
</paginate-source>

<!-- Start a chapter and apply this content to the footer -->
<paginate-source data-key="chapter">CHAPTER 1</paginate-source>
<p>This is my first page content</p>

<!-- Add a page break -->
{{ better_page_break() }}

<!-- Start a second chapter and apply this content to the footer -->
<paginate-source data-key="chapter">CHAPTER 2</paginate-source>
<p>This is my second page content</p>
```

### Header Source Element

Header is a reserved keyword and will automatically add it's content to the main header div. You can use it like this:

```html
<paginate-source data-key="header">
    <!-- Add my Header Content here -->
</paginate-source>
```

### Footer Source Element

Footer is a reserved keyword and will automatically add it's content to the main footer div. You can use it like this:

```html
<paginate-source data-key="footer">
    <!-- Add my Footer Content here -->
</paginate-source>
```

### Page numbers

Page Numbers are a reserved Source keyword and will be set automatically. In order to add page numbers, you'll just need to add this into your header:

```html
<paginate-target data-key="pageNumber"></paginate-source>
<paginate-target data-key="totalPages"></paginate-source>
```

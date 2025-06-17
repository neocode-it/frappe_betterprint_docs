---
description: >-
  Let's try to use some basic & helpful features in Frappe Betterprint you need
  to know.
icon: circle-chevron-right
---

# Betterprint-specific Jinja examples

### Add Page Break

Betterprint comes with a easy-to use page-break - just add this line to your Print Format Jinja:

```django
{{ better_page_break() }}
```

{% hint style="info" %}
CSS can still be used page breaks, just set [break-before](https://developer.mozilla.org/de/docs/Web/CSS/break-before), [break-after](https://developer.mozilla.org/de/docs/Web/CSS/break-after) or [break-inline](https://developer.mozilla.org/de/docs/Web/CSS/break-inside) property.
{% endhint %}

### Add a header with 5cm height

In order to add a header, you can use a `paginate-source` element with `data-key="header"` :

```html
<paginate-source data-key="header"><h1>This is my Header</h1></paginate-source>
```

You can set the header's height by simply adding this css snippet:

```css
.page .header{
    height: 5cm;
    background-color: red;
}
```

### Add a Footer with page number in it

Frappe Betterprint contains two reserved data-source keywords: `pageNumber`and `totalPages` . In order to use these, simply add this Jinja:

```html
<paginate-source data-key="footer">
    <p>Page <paginate-target data-key="pageNumber"></paginate-target> of <paginate-target data-key="totalPages"></paginate-target></p>
<paginate-source>
```

### Set individual Page size

Betterprint allows fully custom page sizes. Even really large sheets will be no problem. You can define your page size as follows:

```css
/* Let's set the page size to A3 format */
.page{
    width: 29.7cm;
    height: 42cm;
}
```

{% hint style="warning" %}
You need to specify the page size using width and height. Passing any page size like A4 or Letter won't work as of now.
{% endhint %}

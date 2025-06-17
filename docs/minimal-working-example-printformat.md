---
description: >-
  Get to know how Betterprint works with this minimal example Printformat which
  includes helpful comments in order to understand how Betterprint should be
  used best.
icon: check
---

# Minimal working example Printformat

#### Print HTML

```django
{# Let's first add a header. In order to accomplish this, #}
{# we simply need to wrap our header with the paginate element #}
<paginate-source data-key="header">
    <img class="logo" src="https://fastly.picsum.photos/id/870/700/300.jpg?blur=2&grayscale&hmac=LQj4SmpDtFvU9sCkzydU_qHD7snZH8XAJ6s1pLGhZLo">
    <h1 class="title">{{doc.name}}</h1>
</paginate-source>


{# Let's add a footer too. Just replace the data-key with footer #}
<paginate-source data-key="footer">
    <p>
        My Test Company<br>
        Street 1<br>
        2332 Test<br>
        TAX-232323343434
    </p>
</paginate-source>


{# Add content as easy as this. Note: Betterprint adds them automatically. #}
<table class="item-table">
    <thead>
        <tr>
            <th style="width: 1cm">#</th>
            <th>Item</th>
            <th style="width: 1.5cm">Qty</th>
            <th style="width: 2cm">Rate</th>
            <th style="width: 2cm">Amount</th>
        </tr>
    </thead>
    <tbody>
        {% raw %}
{% for row in doc.items %}
        <tr>
            <td>{{ row.idx }}</td>
            <td>
                <b>{{ row.item_name }}</b><br>
                {{ row.description }}
            </td>
            <td>{{ row.qty }} {{ row.uom or row.stock_uom }}</td>
            <td>{{ row.get_formatted("rate", doc) }}</td>
            <td>{{ row.get_formatted("amount", doc) }}</td>
        </tr>
        {% endfor %}
{% endraw %}
    </tbody>
</table>
```

#### Print  CSS

```css
.page{
    width: 21cm; /* A4 Page size */
    height: 29.7cm;

    padding: .5cm 2cm;    /* Add some space on the page */
}
.page .header{
    position: relative;
    height: 10cm;    /* Set header height to 10cm height */
}
.page .footer{
    height: 2cm; /* Footer needs to be 2cm heigh */
}

/* Logo & title style within the header */
.logo{
    position: absolute;
    left: 20mm;
    top: 5mm;
    width: 90mm;
}
.title{
    position: absolute;
    top: 6cm;
    left: 10cm;
}

/* Decoration for the table :) */
.page .content{
    .item-table{
        width: 100%;
        color: unset;
        th, td{
            color: black;
            padding: 5px !important;
        }

        thead{
            border-bottom: 1px solid black;
        }
    }
}
```


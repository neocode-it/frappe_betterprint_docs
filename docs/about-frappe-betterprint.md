---
description: Get to know more about Frappe Betterprint...
icon: circle-info
---

# About Frappe Betterprint

### Why another Print solution for Frappe?

When we first considered Frappe Framework for our company, Print Formats have been quite limited. wkhtmltopdf isn't maintained anymore and frappe\_pdff as well as Print Designer is still somewhere limited for specific needs. This lead us to the decision to develop a better solution.

Frappe Betterprint is OpenSource and [available on Github - Contributions are Welcome!](https://github.com/neocode-it/frappe_betterprint)

### How is Betterprint working under the hood?

Frappe Betterprint is heavily relying on an extended version of [paginate.js](https://github.com/neocode-it/paginatejs), which renders the html content into pages. This library has solely been developed for Frappe Betterprint. Besides this library, Betterprint is relying on [Playwright python](https://github.com/microsoft/playwright-python) to control a headless, chromium based browser and create PDF files.

### Who's behind Frappe Betterprint?

Frappe Betterprint has been developed & is maintained by [Neocode.ch](https://neocode.ch), a Company located in Switzerland.

### Contact

Have you found any security concerns or urgent need? Feel free to contact us:

info@neocode.ch

---
description: >-
  Frappe Betterprint can be installed like any other Frappe app too - it's
  straightforward!
icon: down-to-bracket
---

# Installation & Setup

### Installation

Install all required apt-dependencies on your System. These will be required to launch & run Chromium browser (PDF-generation).

```sh
$ sudo apt-get update && \
sudo apt-get install -y libasound2 libatk-bridge2.0-0 \
libatk1.0-0 libatspi2.0-0 libcairo2 libcups2 libdbus-1-3 \
libdrm2 libgbm1 libglib2.0-0 libnspr4 libnss3 libpango-1.0-0 \
libx11-6 libxcb1 libxcomposite1 libxdamage1 libxext6 libxfixes3 \
libxkbcommon0 libxrandr2 xvfb fonts-noto-color-emoji fonts-unifont \
libfontconfig1 libfreetype6 xfonts-scalable fonts-liberation \
fonts-ipafont-gothic fonts-wqy-zenhei fonts-tlwg-loma-otf fonts-freefont-ttf
```

Next, we can get & install our Betterprint app int the frappe system:

```sh
// Get the app on our instance
bench get-app https://github.com/neocode-it/frappe_betterprint

// Install & activate Frappe Betterprint on our site (replace MYSITE with your site)
bench --site MYSITE install-app frappe_betterprint
```

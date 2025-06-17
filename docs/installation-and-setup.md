---
description: >-
  Since Frappe Betterprint depends on chromium, the installation is a little
  more complex. We tried to make the setup process as quick as possible.
icon: down-to-bracket
---

# Installation & Setup

The setup process on a single-machine differs from Docker multi-container setups. Take a look at your required Installation steps:

### Frappe Cloud, local setup or single-container setup

#### Install apt dependencies

Install all required apt-dependencies on your System. These will be required to launch & run Chromium browser (PDF-generation).

```
$ sudo apt-get update && \
sudo apt-get install -y libasound2 libatk-bridge2.0-0 \
libatk1.0-0 libatspi2.0-0 libcairo2 libcups2 libdbus-1-3 \
libdrm2 libgbm1 libglib2.0-0 libnspr4 libnss3 libpango-1.0-0 \
libx11-6 libxcb1 libxcomposite1 libxdamage1 libxext6 libxfixes3 \
libxkbcommon0 libxrandr2 xvfb fonts-noto-color-emoji fonts-unifont \
libfontconfig1 libfreetype6 xfonts-scalable fonts-liberation \
fonts-ipafont-gothic fonts-wqy-zenhei fonts-tlwg-loma-otf fonts-freefont-ttf
```

#### Install Frappe Betterprint & Chromium

After that, we can setup & Install Frappe Betterprint using this command:

```sh
// Get the app on our instance
bench get-app https://github.com/neocode-it/frappe_betterprint

// Install latest chromium binaries
bench setup-betterprint

// Install & activate Frappe Betterprint on our site (replace MYSITE with your site)
bench --site MYSITE install-app frappe_betterprint
```

### Docker Multi-container setup

In order to get Frappe Betterprint working on multi-container setups, it's important that Chromium and it's required packages are installed on all container (Backend, Scheduler & Worker). The simplest way is to append these commands to at the end of your custom Dockerfile. These steps will install all dependencies and the latest & tested Chromium version at built time:

```docker
USER root
RUN sudo apt-get update && \
sudo apt-get install -y libasound2 libatk-bridge2.0-0 \
libatk1.0-0 libatspi2.0-0 libcairo2 libcups2 libdbus-1-3 \
libdrm2 libgbm1 libglib2.0-0 libnspr4 libnss3 libpango-1.0-0 \
libx11-6 libxcb1 libxcomposite1 libxdamage1 libxext6 libxfixes3 \
libxkbcommon0 libxrandr2 xvfb fonts-noto-color-emoji fonts-unifont \
libfontconfig1 libfreetype6 xfonts-scalable fonts-liberation \
fonts-ipafont-gothic fonts-wqy-zenhei fonts-tlwg-loma-otf fonts-freefont-ttf
USER frappe
RUN bench setup-betterprint
```


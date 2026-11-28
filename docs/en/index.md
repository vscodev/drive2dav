---
# https://vitepress.dev/reference/default-theme-home-page
layout: home

hero:
  name: "Drive2dav"
  text: "A lightweight WebDAV server that supports multiple storages"
  image:
    src: /logo.png
    alt: Drive2dav
  actions:
    - theme: brand
      text: Get Started
      link: /en/guide/getting-started
    - theme: alt
      text: GitHub
      link: https://github.com/vscodev/drive2dav

features:
  - title: Multiple storages
    icon: ☁️
    details: Supports popular cloud drive services in China and worldwide, so you can manage the files of all your drives in one place.
  - title: Secure and reliable
    icon: ✅
    details: Built on official open APIs. Tokens are refreshed locally to keep the service running stably.
  - title: Friendly to cloud drive providers
    icon: 🌱
    details: The file index greatly reduces the request rate against cloud drive APIs, which helps you stay clear of rate limiting.
  - title: File Vault
    icon: 🔒
    details: Encrypts your files to protect your privacy; Drive2dav decrypts them automatically when you view or play them.
---

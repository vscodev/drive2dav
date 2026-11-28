---
# https://vitepress.dev/reference/default-theme-home-page
layout: home

hero:
  name: "Drive2dav"
  text: "一个支持多种存储的轻量 WebDAV 服务器"
  image:
    src: /logo.png
    alt: Drive2dav
  actions:
    - theme: brand
      text: 快速开始
      link: /guide/getting-started
    - theme: alt
      text: GitHub
      link: https://github.com/vscodev/drive2dav

features:
  - title: 多种存储
    icon: ☁️
    details: 适配海内外主流的网盘服务，在一个地方聚合管理你所有云盘的文件。
  - title: 安全可靠
    icon: ✅
    details: 基于官方开放 API 开发，令牌刷新在本地进行，确保服务稳定运行。
  - title: 云盘服务商友好
    icon: 🌱
    details: 通过文件索引机制大幅降低对网盘 API 的请求频率，有效应对风控问题。
  - title: 文件保险箱
    icon: 🔒
    details: 对文件加密以保护你的隐私，Drive2dav 会在你阅览/播放时自动解密。
---

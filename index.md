---
layout: home
title: tr4v3ler
cover: true
---

**一名鸿蒙系统与安卓系统内核安全研究员，目前就职于华为。**

---

## 研究方向

- **HarmonyOS 安全研究**：系统架构分析、安全机制研究
- **Android 安全研究**：漏洞挖掘、逆向分析、安全加固
- **移动安全工具开发**：自动化分析工具、调试工具

---

## 文章列表

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url | relative_url }})
{% endfor %}

---

> "Security is not a product, but a process."

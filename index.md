---
layout: default
title: LLM Research Wiki
---

# 🧠 LLM Research Wiki

> AI/ML/NLP/CV 科研知识库 - 由 LLM 自动维护

## 📊 统计信息

- 最后更新: {{ site.time | date: "%Y-%m-%d" }}
- 论文数量: {{ site.pages | where_exp: "page", "page.type == 'paper'" | size }}

## 📚 论文库

{% assign papers = site.pages | where_exp: "page", "page.type == 'paper'" | sort: "published" | reverse %}

{% if papers.size > 0 %}
| 标题 | 分类 | 日期 |
|------|------|------|
{% for paper in papers %}
| [{{ paper.title }}]({{ site.baseurl }}{{ paper.url }}) | {{ paper.tags | join: ", " }} | {{ paper.published }} |
{% endfor %}
{% else %}
暂无论文
{% endif %}

## 📖 使用说明

### 每日自动更新

每天丹麦时间 08:00 自动获取 arXiv 论文并更新知识库。

### 访问方式

- **GitHub Pages:** {{ site.url }}{{ site.baseurl }}/
- **GitHub 仓库:** https://github.com/yhn-liu/LLM-Research-Wiki

---

*Powered by Hermes Agent + Karpathy's LLM Wiki Pattern*

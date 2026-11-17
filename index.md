---
layout: default
title: Statsletters
---

<style>
  body {
    background-image: url("/images/vignette_background.png");
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
    background-repeat: no-repeat;
  }

  .site-header-banner {
    width: 100%;
    max-width: 900px;
    display: block;
    margin: 0 auto 2rem auto;
  }
</style>

<img src="/images/header.png" alt="Statsletters Header" class="site-header-banner" />

{% assign blog_pages = site.pages | where_exp: "p", "p.path contains 'posts/'" | sort: "date" | reverse %}
{% for item in blog_pages %}
  {% unless item.name == 'index.md' %}
## [{{ item.title | default: item.name }}]({{ item.url }})
{% if item.date %}*{{ item.date | date: "%B %-d, %Y" }}*{% endif %}

{{ item.description | default: item.excerpt }}

[Read full post →]({{ item.url }})

---
  {% endunless %}
{% endfor %}
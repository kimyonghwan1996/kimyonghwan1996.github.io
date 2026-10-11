---
layout: page
title: 개인 프로젝트
icon: fas fa-flask
order: 3
mermaid: true
---
{%- assign personals = site.data.career | where: "type", "personal" %}
{% for e in personals %}
### {{ e.project }}

**Stack** {{ e.stack | join: " · " }}

{{ e.summary }}

{% for a in e.achievements -%}
- {{ a }}
{% endfor %}
{% if e.architecture %}
```mermaid
{{ e.architecture }}
```
{% endif %}
{% if e.github %}[GitHub]({{ e.github }}){% endif %}
{% endfor %}

---
layout: page
title: 개인 프로젝트
icon: fas fa-flask
order: 3
mermaid: true
excerpt_separator: ""
---
{%- assign personals = site.data.career | where: "type", "personal" %}
{%- for e in personals %}
<article class="cv-card" markdown="1">
  <h3>{{ e.project }}</h3>
  <div class="cv-stack">{% for s in e.stack %}<span>{{ s }}</span>{% endfor %}</div>
  <p class="cv-summary">{{ e.summary }}</p>
  <ul class="cv-achv">
  {%- for a in e.achievements %}
    <li>{{ a }}</li>
  {%- endfor %}
  </ul>
{%- capture flow_path %}/assets/flows/{{ e.id }}.html{% endcapture %}
{%- assign flow = site.static_files | where: "path", flow_path | first %}
{%- if flow %}
  <iframe class="cv-flow" src="{{ flow_path | relative_url }}" title="{{ e.project }} 흐름 다이어그램" loading="lazy"></iframe>
{%- elsif e.architecture %}

```mermaid
{{ e.architecture }}
```

{%- endif %}
{%- if e.github %}
  <a class="cv-github" href="{{ e.github }}" target="_blank" rel="noopener">GitHub →</a>
{%- endif %}
</article>
{%- endfor %}

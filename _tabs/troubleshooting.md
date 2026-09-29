---
layout: page
title: 트러블슈팅
icon: fas fa-screwdriver-wrench
order: 2
---
{%- assign ts_count = 0 -%}
{%- for e in site.data.career -%}
{%- if e.troubleshooting -%}{%- assign ts_count = ts_count | plus: e.troubleshooting.size -%}{%- endif -%}
{%- endfor %}

문제 → 원인·조치 → 결과 · 총 {{ ts_count }}건

{% if ts_count == 0 -%}
정리 중
{%- endif %}
{% for e in site.data.career %}{% if e.troubleshooting %}
### {{ e.project }} · {{ e.company }}

{% for t in e.troubleshooting -%}
- {{ t.problem }} → {{ t.fix }} → **{{ t.result }}**
{% endfor %}
{% endif %}{% endfor %}

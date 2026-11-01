---
layout: page
title: 트러블슈팅
icon: fas fa-screwdriver-wrench
order: 2
excerpt_separator: ""
---
{%- assign ts_count = 0 -%}
{%- for e in site.data.career -%}
{%- if e.troubleshooting -%}{%- assign ts_count = ts_count | plus: e.troubleshooting.size -%}{%- endif -%}
{%- endfor %}

<p class="cv-ts-count">문제 → 원인·조치 → 결과 · 총 {{ ts_count }}건</p>

{%- if ts_count == 0 %}
정리 중
{%- endif %}
{%- for e in site.data.career %}{% if e.troubleshooting %}
### {{ e.project }}

<div class="cv-ts">
{%- for t in e.troubleshooting %}
  <dl class="cv-ts-item">
    <dt>문제</dt><dd>{{ t.problem }}</dd>
    <dt>조치</dt><dd>{{ t.fix }}</dd>
    <dt>결과</dt><dd class="cv-result">{{ t.result }}</dd>
  </dl>
{%- endfor %}
</div>
{% endif %}{% endfor %}

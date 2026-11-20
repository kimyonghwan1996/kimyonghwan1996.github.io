---
layout: page
title: 경력기술서
icon: fas fa-briefcase
order: 1
excerpt_separator: ""
---
{%- assign p = site.data.profile -%}
{%- assign works = site.data.career | where: "type", "work" -%}
{%- assign personals = site.data.career | where: "type", "personal" -%}
{%- assign ts_count = 0 -%}
{%- for e in site.data.career -%}
{%- if e.troubleshooting -%}{%- assign ts_count = ts_count | plus: e.troubleshooting.size -%}{%- endif -%}
{%- endfor %}

<section class="cv-hero">
  <h2 class="cv-name">{{ p.name }}</h2>
  <p class="cv-headline">{{ p.headline }}</p>
  <ul class="cv-intro">
  {%- for line in p.intro %}
    <li>{{ line }}</li>
  {%- endfor %}
  </ul>
  <div class="cv-links">
    <a href="mailto:{{ p.email }}">{{ p.email }}</a>
    <a href="https://github.com/{{ p.github }}" target="_blank" rel="noopener">GitHub</a>
    <a href="{{ '/projects/' | relative_url }}">개인 프로젝트 <span class="cv-count">{{ personals.size }}</span></a>
    <a href="{{ '/troubleshooting/' | relative_url }}">트러블슈팅 <span class="cv-count">{{ ts_count }}</span></a>
  </div>
</section>

## 경력

<ol class="cv-timeline">
{%- for c in p.careers %}
  <li>
    <span class="cv-period">{{ c.period }}</span>
    <div><div class="cv-company">{{ c.company }}</div><div class="cv-role">{{ c.role }}{% if c.desc %} · {{ c.desc }}{% endif %}</div></div>
  </li>
{%- endfor %}
</ol>

## 업무 프로젝트

{%- for e in works %}
<article class="cv-card">
  <h3>{{ e.project }}</h3>
  <p class="cv-meta"><span>{{ e.company }}</span>{% if e.client %}<span>{{ e.client }}</span>{% endif %}<span>{{ e.period }}</span><span>{{ e.role | join: ", " }}</span></p>
  <div class="cv-stack">{% for s in e.stack %}<span>{{ s }}</span>{% endfor %}</div>
  <p class="cv-summary">{{ e.summary }}</p>
  <ul class="cv-achv">
  {%- for a in e.achievements %}
    <li>{{ a }}</li>
  {%- endfor %}
  </ul>
</article>
{%- endfor %}

## 학력 · 교육 · 자격

<div class="cv-grid">
  <div>
    <h4>학력</h4>
    <ul>{% for x in p.education %}<li>{{ x.name }} <span class="cv-when">{{ x.period }}</span></li>{% endfor %}</ul>
  </div>
  <div>
    <h4>교육</h4>
    <ul>{% for x in p.training %}<li>{{ x.name }} <span class="cv-when">{{ x.period }}</span></li>{% endfor %}</ul>
  </div>
  <div>
    <h4>자격</h4>
    <ul>{% for x in p.certifications %}<li>{{ x.name }} <span class="cv-when">{{ x.date }}</span></li>{% endfor %}</ul>
  </div>
</div>

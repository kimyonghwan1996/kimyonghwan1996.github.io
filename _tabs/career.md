---
layout: page
title: 경력기술서
icon: fas fa-briefcase
order: 1
mermaid: true
---
{%- assign p = site.data.profile -%}
{%- assign works = site.data.career | where: "type", "work" -%}
{%- assign personals = site.data.career | where: "type", "personal" %}

**{{ p.headline }}**

{% for line in p.intro -%}
- {{ line }}
{% endfor %}
이메일 [{{ p.email }}](mailto:{{ p.email }}) · GitHub [{{ p.github }}](https://github.com/{{ p.github }})

## 경력

{% for c in p.careers -%}
- **{{ c.company }}** · {{ c.role }} · {{ c.period }}{% if c.desc %} — {{ c.desc }}{% endif %}
{% endfor %}

## 업무 프로젝트
{% for e in works %}
### {{ e.project }}

{{ e.company }}{% if e.client %} · {{ e.client }}{% endif %} · {{ e.period }} · {{ e.role | join: ", " }}
{: .text-muted }

**Stack** {{ e.stack | join: " · " }}

{{ e.summary }}

{% for a in e.achievements -%}
- {{ a }}
{% endfor %}
{% endfor %}

## 개인 프로젝트
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

## 트러블슈팅

{% assign ts_count = 0 -%}
{% for e in site.data.career -%}
{% if e.troubleshooting %}{% assign ts_count = ts_count | plus: e.troubleshooting.size %}{% endif -%}
{% endfor -%}
{% if ts_count == 0 %}- 정리 중
{% endif -%}
{% for e in site.data.career -%}
{% for t in e.troubleshooting -%}
- **[{{ e.project }}]** {{ t.problem }} → {{ t.fix }} → **{{ t.result }}**
{% endfor -%}
{% endfor %}

## 학력 · 교육 · 자격

{% for x in p.education -%}
- {{ x.name }} · {{ x.period }}
{% endfor %}
{% for x in p.training -%}
- {{ x.name }} · {{ x.period }}
{% endfor %}
{% for x in p.certifications -%}
- {{ x.name }} · {{ x.date }}
{% endfor %}

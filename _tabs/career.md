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
{% if e.troubleshooting %}
**트러블슈팅**

{% for t in e.troubleshooting -%}
- **문제** {{ t.problem }} → **조치** {{ t.fix }} → **결과** {{ t.result }}
{% endfor %}
{% endif %}
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

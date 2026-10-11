---
layout: page
title: 경력기술서
icon: fas fa-briefcase
order: 1
---
{%- assign p = site.data.profile -%}
{%- assign works = site.data.career | where: "type", "work" -%}
{%- assign personals = site.data.career | where: "type", "personal" -%}
{%- assign ts_count = 0 -%}
{%- for e in site.data.career -%}
{%- if e.troubleshooting -%}{%- assign ts_count = ts_count | plus: e.troubleshooting.size -%}{%- endif -%}
{%- endfor %}

**{{ p.headline }}**

{% for line in p.intro -%}
- {{ line }}
{% endfor %}
이메일 [{{ p.email }}](mailto:{{ p.email }}) · GitHub [{{ p.github }}](https://github.com/{{ p.github }}) · [개인 프로젝트 {{ personals.size }}건 →]({{ '/projects/' | relative_url }}) · [트러블슈팅 {{ ts_count }}건 →]({{ '/troubleshooting/' | relative_url }})

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

---
layout: single
title: Profiles
permalink: /profiles/
---

# Another profiles

{% include_relative _templates/warning.liquid content="All profiles on Russian resources are now deprecated and no more longer used" %}

{% for profile in site.data.profiles %}
    {%- assign visible = true -%}
    {%- if profile.visible == false -%}
        {%- assign visible = profile.visible -%}
    {%- endif -%}
    {%- if visible == true -%}
        {%- assign name = profile.name -%}
        {%- assign url = profile.url %}
- [{{ name }}]({{ url }})
    {%- endif -%}
{% endfor %}

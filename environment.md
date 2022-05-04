---
layout: single
title: Environment
permalink: /environment/
---

# My preferences

{% assign left_color = "58158f" -%}
{%- assign right_color = "000000" -%}
{%- assign logo_color = "e9e0ff" -%}

{% for config in site.data.configs %}
    {%- assign visible = true -%}
    {%- if config.visible == false -%}
        {%- assign visible = config.visible -%}
    {%- endif -%}
    {%- if visible -%}
        {%- assign name = config.name | escape -%}
        {%- assign application = config.application -%}
        {%- assign url = config.url | escape -%}
        {%- assign logo = config.logo -%}
        {%- assign params = "" -%}
        {%- if logo -%}
            {%- assign params = params | append: "&logo=" | append: logo | append: "&logoColor=" | append: logo_color -%}
        {%- endif -%}
[![{{ name }}](https://img.shields.io/badge/{{ name }}-{{ application }}-{{ right_color }}?labelColor={{ left_color }}{{ params }})]({{ url }})
    {% endif -%}
{% endfor %}

![Language logos](/images/environment.png)

- `OS`: Ubuntu Mate 20.04.4 LTS
- `Shell`: Zsh
- `Editor`: Vim

## Favourite Visual Studio Code extensions

{% include_relative _templates/link_bullet_list.liquid items=site.data.code_extensions %}

## Favourite Vim extensions

{% include_relative _templates/info.liquid content="This extension list is going to be refreshed." %}

{% include_relative _templates/link_bullet_list.liquid items=site.data.vim_extensions %}

---
layout: single
title: About me
permalink: /about/

background_music: Eternals - Final Trailer Music
---

# Summary

{% include_relative _templates/tool_badge_list.liquid items=site.data.languages -%}
|
{% include_relative _templates/tool_badge_list.liquid items=site.data.editors -%}
|
{% include_relative _templates/tool_badge_list.liquid items=site.data.vcs %}

My name is `Emily Grace Seville`. I am a native russian speaker, open source contributor and I keen on scripting. It's my life. I like to automate routine tasks and not to do them manually. More often I use `Zsh`/`Bash` and other languages for this purpose because they are simple to learn and use.

I don't think my knowledge are perfect but I believe they are good enough to make my life and other's ones better. :smile:

![Language logos](/images/about.jpg)

![Emily Seville's GitHub stats](https://github-readme-stats.vercel.app/api?username=EmilySeville7cfg&count_private=true&show_icons=true&theme=tokyonight)

[View more statistics about myself](https://www.githubtrends.io/wrapped/EmilySeville7cfg)

## Favourite tools

| Project     | Description                                  |
| :---------- | :------------------------------------------- |
| `Zsh`       | User-friendly non-POSIX compliant shell      |
| `Bash`      | POSIX compliant replacement for Bourne shell |
| `Oh My Zsh` | Framework for customizing Zsh shell          |
| `Tl;Dr`     | Simple practical-oriented help pages         |

## Archivements

{% for achievement in site.data.achievements %}
    {%- assign visible = true -%}
    {%- if achievement.visible == false -%}
        {%- assign visible = achievement.visible -%}
    {%- endif -%}
    {%- if visible -%}
        {%- assign description = achievement.description -%}
        {%- assign date = achievement.date %}
- {{ date }}: **{{ description }}**
    {%- endif -%}
{% endfor %}

### My organizations

{% include_relative _templates/link_bullet_list.liquid items=site.data.organizations %}

# Unused languages and tools

The following languages and tools are not required for my tasks and that’s why I don’t remember them very well:

{% include_relative _templates/tool_badge_list.liquid items=site.data.unused_languages -%}
|
{% include_relative _templates/tool_badge_list.liquid items=site.data.unused_vcs -%}

# All presentations about me

{% include_relative _templates/warning.liquid content="All presentations have many animations. Please use `Slideshow` to view them." %}

{% include_relative _templates/link_bullet_list.liquid items=site.data.presentations %}

{% for music in site.static_files %}
    {% if music.path contains page.background_music %}
> {{ music.name | remove: ".mp3" }}
<embed name="Background music" src="{{ music.path }}" loop="true" hidden="true" autostart="true">
        {% break %}
    {% endif %}
{% endfor %}

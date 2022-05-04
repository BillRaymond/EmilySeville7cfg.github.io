---
layout: single
title: Games
permalink: /games/
---

## Favourite games

| Game | Description |
| :--- | :---------- |
{% for game in site.games -%}
| [{{ game.title }}]({{ game.url }}) | {{ game.description }} |
{% endfor %}

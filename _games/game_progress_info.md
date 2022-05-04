{%- assign money = "unspecified" -%}
{%- if page.money -%}
    {%- assign money = page.money -%}
{%- endif -%}

{%- assign cars = "unspecified" -%}
{%- if page.cars -%}
    {%- assign cars = page.cars | join: "**, **" | prepend: "**" | append: "**" -%}
{%- endif -%}

{%- assign tracks = "unspecified" -%}
{%- if page.tracks -%}
    {%- assign tracks = page.tracks | join: "**, **" | prepend: "**" | append: "**" -%}
{%- endif %}

| :moneybag: Money amount | :car: Available cars | :motorway: Available tracks |
| :---------------------: | :------------------- | :-------------------------- |
|       {{ money }}       | {{ cars }}           | {{ tracks }}                |
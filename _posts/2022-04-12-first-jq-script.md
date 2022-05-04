---
layout: single
title: "My first jq script!"
date: 2022-04-12 11:15:00 +1000
categories: news scripting jq
---

# Summary

I've just wrote a simple `jq` script to:

- remove unnecessary top-level keys
- sort all keys in the following order:
  - `$comment`
  - `title`
  - `description`
  - `type`
  - `default`
  - `required`

It helps me standardize JSON schemas quickly.

```sh
#!/usr/bin/env bash

jq 'walk(
    if type == "object" then
        if has("required") then
            . = { required } + .
        else
            .
        end | if has("default") then
            . = { default } + .
        else
            .
        end | if has("type") then
            . = { type } + .
        else
            .
        end | if has("description") then
            . = { description } + .
        else
            .
        end | if has("title") then
            . = { title } + .
        else
            .
        end | if has("$comment") then
            . = { "$comment" } + .
        else
            .
        end
    else
        .
    end
) | {
  "$comment",
  "$schema": "http://json-schema.org/draft-07/schema",
  "title": "PLACEHOLDER config file schema",
  "type": "PLACEHOLDER"
} + . | delpaths([["description"]])' input.json
```

Input json:

```json
{
  "title": "JSON schema for Google Apps Script project files",
  "description": "ERROR",
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "scriptId": {
      "description": "The ID of the Apps Script project",
      "type": "string",
      "minLength": 57,
      "maxLength": 57
    },
    "rootDir": {
      "description": "The relative path to the custom root directory to your Apps Script files.",
      "default": ".",
      "type": "string"
    },
    "projectId": {
      "description": "The ID for the Google Cloud Platform project linked to this script",
      "default": "project-id-xxxxxxxxxxxxxxxxxxx",
      "type": "string",
      "minLength": 4,
      "maxLength": 30
    }
  },
  "$comment": "TEST"
}
```

Output:

```json
{
  "$comment": "TEST",
  "$schema": "http://json-schema.org/draft-04/schema#",
  "title": "JSON schema for Google Apps Script project files",
  "type": "object",
  "properties": {
    "scriptId": {
      "description": "The ID of the Apps Script project",
      "type": "string",
      "minLength": 57,
      "maxLength": 57
    },
    "rootDir": {
      "description": "The relative path to the custom root directory to your Apps Script files.",
      "type": "string",
      "default": "."
    },
    "projectId": {
      "description": "The ID for the Google Cloud Platform project linked to this script",
      "type": "string",
      "default": "project-id-xxxxxxxxxxxxxxxxxxx",
      "minLength": 4,
      "maxLength": 30
    }
  }
}
```

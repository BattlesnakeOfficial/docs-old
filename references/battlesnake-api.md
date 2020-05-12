---
description: Official Reference for the Battlesnake API (Version 1)
---

# Battlesnake API

The Battlesnake API is an inverted HTTP API. Developers implement this API and the game engine will make HTTP requests to your server during each game. How your server responds will control how your Battlesnake behaves.

{% api-method method="get" host="https://your.battlesnake.server.com" path="/" %}
{% api-method-summary %}
/
{% endapi-method-summary %}

{% api-method-description %}
This command is used by the game engine to retrieve information about your Battlesnake, including its author and display options.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
application/json
{% endapi-method-response-example-description %}

```javascript
{
    "apiversion": "1",
    "author": "your-username",
    "color": "#888888",
    "head": "default",
    "tail": "default"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameters**

| **Parameter** | **Type** | **Description** |
| :--- | :--- | :--- |
| **apiversion** | string | Version of the Battlesnake API implemented by this Battlesnake. |
| **author** | string \(optional\) | Username of the author of this Battlesnake. If provided, this will be used to verify ownership. |
| **color** | string \(optional\) | Hex color code used to display this Battlesnake. Must start with "\#" and be 7 characters long.  |
| **head** | string \(optional\) | Displayed head of this Battlesnake. See REFERENCE HERE for available options. |
| **tail** | string \(optional\) | Displayed tail of this Battlesnake. See REFERENCE HERE for available options. |




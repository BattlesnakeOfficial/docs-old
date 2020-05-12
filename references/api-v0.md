---
description: Reference for the HTTP API implemented by Battlesnakes
---

# Battlesnake API \(v0\)

{% hint style="warning" %}
**This API version has been deprecated.**

Please upgrade your Battlesnakes to use the Battlesnake API v1.
{% endhint %}

{% api-method method="get" host="https://your-battlesnake.com" path="/ping" %}
{% api-method-summary %}
Ping
{% endapi-method-summary %}

{% api-method-description %}
A heartbeat call to check if your snake server is running.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Response body is ignored
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://your-battlesnake.com" path="/start" %}
{% api-method-summary %}
Start New Game
{% endapi-method-summary %}

{% api-method-description %}
Called when your Battlesnake has been entered into a new game.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="you" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="game" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
application/json
{% endapi-method-response-example-description %}

```javascript
{
  "color": "#ff00ff",
  "headType": "bendr",
  "tailType": "pixel"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://your-battlesnake.com" path="/move" %}
{% api-method-summary %}
Take a turn within a game
{% endapi-method-summary %}

{% api-method-description %}
Take a turn within a game
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="you" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="game" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
application/json
{% endapi-method-response-example-description %}

```javascript
{
  "move": "right", 
  "shout": "I am moving left!"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://your-battlesnake.com" path="/end" %}
{% api-method-summary %}
Signal game has ended
{% endapi-method-summary %}

{% api-method-description %}
Signals a game has ended
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="you" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="game" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
  
Response body is ignored.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


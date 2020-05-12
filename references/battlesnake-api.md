---
description: Official Reference for the Battlesnake API (Version 1)
---

# Battlesnake API

The Battlesnake API is an inverted HTTP API. Developers implement this API and the game engine will make HTTP requests to your server during each game. How your server responds will control how your Battlesnake behaves.

## API Object Definitions

The game engine uses the following object definitions when communicating with your Battlesnake.

### Game

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| **id** | string | A unique identifier for this Game. |
| **timeout** | integer \(milliseconds\) | How much time your snake has to respond to requests for this Game. |

{% code title="Example Game Object" %}
```javascript
{
  "id": "unique-game-id",
  "timeout": 500
}
```
{% endcode %}

### Battlesnake

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| **id** | string | Unique identifier for this Battlesnake in the context of the current Game. |
| **name** | string | Name given to this Battlesnake by its author. |
| **health** | integer | Health value of this Battlesnake, between 0 and 100 inclusively. |
| **body** | array | Array of coordinates representing this Battlesnake's location on the game board. This array is ordered from head to tail. |
| **head** | object | Coordinates for this Battlesnake's head. Equivalent to the first element of the body array. |
| **tail** | object | Coordinates for this Battlesnake's tail. Equivalent to the last element of the body array. |
| **length** | integer | Length of this Battlesnake from head to tail. Equivalent to the length of the body array. |
| **shout** | string | Message shouted by this Battlesnake on the previous turn. |

{% code title="Example Battlesnake Object" %}
```javascript
{
  "id": ...,
  "name": ...,
  "health": ...,
  "body": ...,
  "head": ...,
  "tail": ...,
  "length": ...,
  "shout": ...
}
```
{% endcode %}

### Board

| **Property** | **Type** | **Description** |
| :--- | :--- | :--- |
| **height** | integer | Height of the game board. |
| **width** | integer | Width of the game board. |
| **food** | array | Array of coordinates representing food locations on the game board. |
| **snakes** | array | Array of \[BATTLESNAKE OBJECTS\] representing all Battlesnakes on the game board \(including yourself if applicable\). |

{% code title="Example Board Object" %}
```javascript
{
  "height": ...,
  "width": ...,
  "food": ...,
  "snakes": ...,
}
```
{% endcode %}

## Battlesnake API Calls

To play Battlesnake your server should implement the following HTTP API Calls.

{% api-method method="get" host="https://your.battlesnake.server.com" path="/" %}
{% api-method-summary %}
/
{% endapi-method-summary %}

{% api-method-description %}
This request will be sent periodically by the game engine to retrieve information about your Battlesnake, including its author and display options.
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

{% api-method method="post" host="https://your.battlesnake.server.com" path="/start" %}
{% api-method-summary %}
/start
{% endapi-method-summary %}

{% api-method-description %}
Your Battlesnake will receive this request when it has been entered into a new game. Every game has a unique ID that can be used to allocate resources or data you may need. Your response to this request will be ignored.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="game" type="object" required=false %}
\[GAME OBJECT\] describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=false %}
Turn number of the game being played \(0 for new games\).
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=false %}
\[BOARD OBJECT\] describing the initial state of the game board.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=false %}
\[SNAKE OBJECT\] describing your Battlesnake.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Responses to this command are ignored by the game engine.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://your.battlesnake.server.com" path="/move" %}
{% api-method-summary %}
/move
{% endapi-method-summary %}

{% api-method-description %}
This request will be sent for every turn of the game. Use the information provided to determine how your Battlesnake will move on that turn, either up, down, left, or right.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="game" type="string" required=false %}
\[GAME OBJECT\] describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=false %}
Turn number for this move.
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=false %}
\[BOARD OBJECT\] describing the game board on this turn.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=false %}
\[SNAKE OBJECT\] describing your Battlesnake.
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
  "move": "up",
  "shout": "I am moving up!"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameters**

| **Parameter** | **Type** | **Description** |
| :--- | :--- | :--- |
| **move** | string | Your Battlesnake's move for this turn. Must be one of "up", "down", "left", or "right". |
| **shout** | string \(optional\) | An optional message sent to all other Battlesnakes on the next turn. Must be 256 characters or less. |

{% api-method method="post" host="https://your.battlesnake.server.com" path="/end" %}
{% api-method-summary %}
/end
{% endapi-method-summary %}

{% api-method-description %}
Your Battlesnake will receive this request whenever a game it was playing has ended. Use it to learn how your Battlesnake won or lost and deallocated any server-side resources. Your response to this request will be ignored.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="game" type="object" required=false %}
\[GAME OBJECT\[ describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=false %}
Turn number for the last turn of this game.
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=false %}
\[BOARD OBJECT\] describing the final turn of this game.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=false %}
\[SNAKE OBJECT\] describing your Battlesnake.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Responses to this command are ignored by the game engine.
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}


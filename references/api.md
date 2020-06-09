---
description: Official Reference for the Battlesnake API (Version 1)
---

# API Reference

## Introduction

The Battlesnake API is an inverted HTTP API. Developers build a web server that implements this API and the game engine will act as an API client during each game. How your server responds to these requests controls how your Battlesnake behaves.

Requests sent to your Battlesnake will be [JSON-encoded](www.json.org), using standard HTTP request methods and content types.

### HTTP Response Codes

All Battlesnake API requests must return a valid _HTTP \`200 OK\`_. If any other status code is returned, the game engine will consider it an error and act accordingly.

### Response Content-Type

All responses must be JSON-encoded strings sent as \`_application/json\`_. If the game engine receives an invalid response from your Battlesnake it will consider it an error and act accordingly.

### Request Timeouts

Every request made to your Battlesnake server must be responded to within the given timeout value. In most standard games this will be 500ms, however this value can vary from game to game. Use the [game information provided](api.md#game) in the request to determine how long your Battlesnake should spend computing its next move.

Note that these values include round-trip latency, so communication between the game engine and your Battlesnake server should be taken into consideration.

## The Battlesnake API

Your Battlesnake server must implement the following HTTP calls to play the game.

{% api-method method="get" host="https://your.battlesnake.server.com" path="/" %}
{% api-method-summary %}
/
{% endapi-method-summary %}

{% api-method-description %}
This request will be made periodically to retrieve information about your Battlesnake, including its display options, author, etc.
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

**Response Properties**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter</b>
      </th>
      <th style="text-align:left"><b>Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>apiversion</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">Version of the Battlesnake API implemented by this Battlesnake.
        <br /><em>Example: &quot;1&quot;</em>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>author</b>
      </td>
      <td style="text-align:left">string <em>(optional)</em>
      </td>
      <td style="text-align:left">
        <p>Username of the author of this Battlesnake. If provided, this will be
          used to verify ownership.</p>
        <p><em>Example: &quot;BattlesnakeOfficial&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b>
      </td>
      <td style="text-align:left">string <em>(optional)</em>
      </td>
      <td style="text-align:left">
        <p>Hex color code used to display this Battlesnake. Must start with &quot;#&quot;
          and be 7 characters long.</p>
        <p><em>Example: &quot;#888888&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>head</b>
      </td>
      <td style="text-align:left">string <em>(optional)</em>
      </td>
      <td style="text-align:left">
        <p>Displayed head of this Battlesnake. See <a href="personalization.md">Personalization Docs</a> for
          available options</p>
        <p><em>Example: &quot;default&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tail</b>
      </td>
      <td style="text-align:left">string <em>(optional)</em>
      </td>
      <td style="text-align:left">
        <p>Displayed tail of this Battlesnake. See <a href="personalization.md">Personalization Docs</a> for
          available options.</p>
        <p><em>Example: &quot;default&quot;</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

See [Personalization Reference](personalization.md) for available colors, heads, and tails.

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
Game Object describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=false %}
Turn number of the game being played \(0 for new games\).
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=false %}
Board Object describing the initial state of the game board.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=false %}
Battlesnake Object describing your Battlesnake.
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

**Response Properties**

Responses to this request are ignored by the game engine.

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
{% api-method-parameter name="game" type="object" required=false %}
Game Object describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=false %}
Turn number for this move.
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=false %}
Board Object describing the game board on this turn.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=false %}
Battlesnake Object describing your Battlesnake.
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

**Response Properties**

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Parameter</b>
      </th>
      <th style="text-align:left"><b>Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>move</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>Your Battlesnake&apos;s move for this turn. Valid moves are up, down,
          left, or right.</p>
        <p><em>Example: &quot;up&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>shout</b>
      </td>
      <td style="text-align:left">string <em>(optional)</em>
      </td>
      <td style="text-align:left">
        <p>An optional message sent to all other Battlesnakes on the next turn. Must
          be 256 characters or less.</p>
        <p><em>Example: &quot;I am moving up!&quot;</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

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
Game Object describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=false %}
Turn number for the last turn of this game.
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=false %}
Board Object describing the final turn of this game.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=false %}
Battlesnake Object describing your Battlesnake.
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

**Response Properties**

Responses to this request are ignored by the game engine.

## Object Definitions

The Battlesnake API uses the following object definitions when communicating with your Battlesnake web server.

### Game

{% code title="example-game-object.json" %}
```javascript
{
  "id": "totally-unique-game-id",
  "timeout": 500
}
```
{% endcode %}

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Property</b>
      </th>
      <th style="text-align:left"><b>Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>id</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>A unique identifier for this Game.</p>
        <p><em>Example: &quot;totally-unique-game-id&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>timeout</b>
      </td>
      <td style="text-align:left">integer <em>(milliseconds)</em>
      </td>
      <td style="text-align:left">
        <p>How much time your snake has to respond to requests for this Game.</p>
        <p><em>Example: 500</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### Battlesnake

{% code title="example-battlesnake-object.json" %}
```javascript
{
  "id": "totally-unique-snake-id",
  "name": "Sneky McSnek Face",
  "health": 54,
  "body": [
    {"x": 0, "y": 0}, 
    {"x": 1, "y": 0}, 
    {"x": 2, "y": 0}
  ],
  "head": {"x": 0, "y": 0},
  "length": 3,
  "shout": "why are we shouting??"
}
```
{% endcode %}

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Property</b>
      </th>
      <th style="text-align:left"><b>Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>id</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>Unique identifier for this Battlesnake in the context of the current Game.</p>
        <p><em>Example: &quot;totally-unique-snake-id&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>Name given to this Battlesnake by its author.</p>
        <p><em>Example: &quot;Sneky McSnek Face&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>health</b>
      </td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">
        <p>Health value of this Battlesnake, between 0 and 100 inclusively.</p>
        <p><em>Example: 54</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>body</b>
      </td>
      <td style="text-align:left">array</td>
      <td style="text-align:left">
        <p>Array of coordinates representing this Battlesnake&apos;s location on
          the game board. This array is ordered from head to tail.</p>
        <p><em>Example: [{&quot;x&quot;: 0, &quot;y&quot;: 0}, ..., {&quot;x&quot;: 2, &quot;y&quot;: 0}]</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>head</b>
      </td>
      <td style="text-align:left">object</td>
      <td style="text-align:left">
        <p>Coordinates for this Battlesnake&apos;s head. Equivalent to the first
          element of the body array.</p>
        <p><em>Example: {&quot;x&quot;: 0, &quot;y&quot;: 0}</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>length</b>
      </td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">
        <p>Length of this Battlesnake from head to tail. Equivalent to the length
          of the body array.</p>
        <p><em>Example: 3</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>shout</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>Message shouted by this Battlesnake on the previous turn.</p>
        <p><em>Example: &quot;why are we shouting??&quot;</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### Board

The game board is represented by a standard 2D grid, oriented with \(0,0\) in the bottom left. The Y-Axis is positive in the up direction, and X-Axis is positive to the right. Coordinates begin at zero, such that a board that is 12x12 will have coordinates ranging from \[0, 11\].

![Battlesnake coordinate system](../.gitbook/assets/11-scale.png)

{% code title="example-board-object.json" %}
```javascript
{
  "height": 11,
  "width": 11,
  "food": [
    {"x": 5, "y": 5}, 
    {"x": 9, "y": 0}, 
    {"x": 2, "y": 6}
  ],
  "snakes": [
    {"id": "snake-one", ... },
    {"id": "snake-two", ... },
    {"id": "snake-three", ... }
  ]
}
```
{% endcode %}

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Property</b>
      </th>
      <th style="text-align:left"><b>Type</b>
      </th>
      <th style="text-align:left"><b>Description</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>height</b>
      </td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">
        <p>Height of the game board.</p>
        <p><em>Example: 11</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>width</b>
      </td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">
        <p>Width of the game board.</p>
        <p><em>Example: 11</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>food</b>
      </td>
      <td style="text-align:left">array</td>
      <td style="text-align:left">
        <p>Array of coordinates representing food locations on the game board.</p>
        <p><em>Example: [{&quot;x&quot;: 5, &quot;y&quot;: 5}, ..., {&quot;x&quot;: 2, &quot;y&quot;: 6}]</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>snakes</b>
      </td>
      <td style="text-align:left">array</td>
      <td style="text-align:left">
        <p>Array of <a href="api.md#battlesnake">Battlesnake Objects</a> representing
          all Battlesnakes remaining on the game board (including yourself if you
          haven&apos;t been eliminated).</p>
        <p><em>Example: [{&quot;id&quot;: &quot;snake-one&quot;, ...}, ...]</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

## Example Move Request

Here's a complete example of a request made to [POST /move](api.md#move) and a valid Battlesnake response to move up.

### Request

{% code title="POST https://your.battlesnake.server.com/move" %}
```javascript
{
  "game": {
    "id": "game-00fe20da-94ad-11ea-bb37",
    "timeout": 500
  },
  "turn": 14,
  "board": {
    "height": 11,
    "width": 11,
    "food": [
      {"x": 5, "y": 5}, 
      {"x": 9, "y": 0}, 
      {"x": 2, "y": 6}
    ],
    "snakes": [
      {
        "id": "snake-508e96ac-94ad-11ea-bb37",
        "name": "My Snake",
        "health": 54,
        "body": [
          {"x": 0, "y": 0}, 
          {"x": 1, "y": 0}, 
          {"x": 2, "y": 0}
        ],
        "head": {"x": 0, "y": 0},
        "length": 3,
        "shout": "why are we shouting??"
      }, 
      {
        "id": "snake-b67f4906-94ae-11ea-bb37",
        "name": "Another Snake",
        "health": 16,
        "body": [
          {"x": 5, "y": 4}, 
          {"x": 5, "y": 3}, 
          {"x": 6, "y": 3},
          {"x": 6, "y": 2}
        ],
        "head": {"x": 5, "y": 4},
        "length": 4,
        "shout": "I'm not really sure..."
      }
    ]
  },
  "you": {
    "id": "snake-508e96ac-94ad-11ea-bb37",
    "name": "My Snake",
    "health": 54,
    "body": [
      {"x": 0, "y": 0}, 
      {"x": 1, "y": 0}, 
      {"x": 2, "y": 0}
    ],
    "head": {"x": 0, "y": 0},
    "length": 3,
    "shout": "why are we shouting??"
  }
}
```
{% endcode %}

### **Response**

{% code title="200 OK" %}
```javascript
{
  "move": "up",
  "shout": "I guess I'll go up then."
}
```
{% endcode %}


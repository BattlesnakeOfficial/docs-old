---
description: Official Reference for the Battlesnake API (Version 1)
---

# API Reference

## Introduction

The Battlesnake API is an inverted HTTP API. Developers build a web server that implements this API and the game engine will act as an API client during each game. How your server responds to these requests controls how your Battlesnake behaves.

Requests sent to your Battlesnake will be [JSON-encoded](https://www.json.org/), using standard HTTP request methods and content types.

### HTTP Response Codes

All Battlesnake API requests must return a valid _HTTP \`200 OK\`_. If any other status code is returned, the game engine will consider it an error and act accordingly.

### Response Content-Type

All responses must be JSON-encoded strings sent as \`_application/json\`_. If the game engine receives an invalid response from your Battlesnake it will consider it an error and act accordingly.

### Request Timeouts

Every request made to your Battlesnake server must be responded to within the given timeout value. In most standard games this will be 500ms, however this value can vary from game to game. Use the [game information provided](./#game) in the request to determine how long your Battlesnake should spend computing its next move.

Note that these values include round-trip latency, so communication between the game engine and your Battlesnake server should be taken into consideration.

## The Battlesnake API

The Battlesnake API consists of four commands. Your Battlesnake server must implement all four HTTP calls to play the game. These commands are called at different times during each game and your response to these command controls how your Battlesnake appears and behaves on the game board.

[**Command: Get Battlesnake**](./#undefined)  
This command is called periodically by the game engine and the Battlesnake platform. It should return information about your Battlesnake, including who created it and what it looks like.

[**Command: Start Game**](./#start)  
This command is called once at the beginning of every game to let your Battlesnake know that a new game is about to start.

[**Command: Move**](./#move)  
This command is called once per turn of each game, providing information about the game board to your Battlesnake and asking for its next move. Your response to this command determines how your Battlesnake behaves and will be the primary focus of your game logic programming.

[**Command: End Game**](./#end)  
This command is called once after each game has completed to let your Battlesnake know that the game is over.



{% api-method method="get" host="https://your.battlesnake.server.com" path="/" %}

```javascript
example-battlesnake-customization.json

{
 "apiversion": "1",
 "author": "MyUsername",
 "color" : "#888888",
 "head" : "default",
 "tail" : "default",
 "version" : "0.0.1-beta"
}
```

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
      <td style="text-align:left">string <em>(required)</em>
      </td>
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
        <p>Displayed head of this Battlesnake. See <a href="../personalization.md">Personalization Docs</a> for
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
        <p>Displayed tail of this Battlesnake. See <a href="../personalization.md">Personalization Docs</a> for
          available options.</p>
        <p><em>Example: &quot;default&quot;</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b>
      </td>
      <td style="text-align:left">string <em>(optional)</em>
      </td>
      <td style="text-align:left">A version number or tag for your snake.</td>
    </tr>
  </tbody>
</table>

See [Personalization Reference](../personalization.md) for available colors, heads, and tails.



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
{% api-method-parameter name="game" type="object" required=true %}
Game Object describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=true %}
Turn number of the game being played \(0 for new games\).
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=true %}
Board Object describing the initial state of the game board.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=true %}
Battlesnake Object describing your Battlesnake.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Responses to this command are ignored by the game engine.
{% endapi-method-response-example-description %}

```text

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
{% api-method-parameter name="game" type="object" required=true %}
Game Object describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=true %}
Turn number for this move.
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=true %}
Board Object describing the game board on this turn.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=true %}
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
{% api-method-parameter name="game" type="object" required=true %}
Game Object describing the game being played.
{% endapi-method-parameter %}

{% api-method-parameter name="turn" type="integer" required=true %}
Turn number for the last turn of this game.
{% endapi-method-parameter %}

{% api-method-parameter name="board" type="object" required=true %}
Board Object describing the final turn of this game.
{% endapi-method-parameter %}

{% api-method-parameter name="you" type="object" required=true %}
Battlesnake Object describing your Battlesnake.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Responses to this command are ignored by the game engine.
{% endapi-method-response-example-description %}

```text

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
      <td style="text-align:left"><b>ruleset</b>
      </td>
      <td style="text-align:left">object</td>
      <td style="text-align:left">
        <p>Information about the ruleset being used to run this game.</p>
        <p><em>Example: {&quot;name&quot;: &quot;standard&quot;, &quot;version&quot;: &quot;v1.2.3&quot;}</em>
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
  "latency": "123",
  "head": {"x": 0, "y": 0},
  "length": 3,
  "shout": "why are we shouting??",
  "squad": "1"
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
      <td style="text-align:left"><b>latency</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>The previous response time of this Battlesnake, in milliseconds. &quot;0&quot;
          means the Battlesnake timed out and failed to respond.</p>
        <p><em>Example: &quot;450&quot;</em>
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
    <tr>
      <td style="text-align:left"><b>squad</b>
      </td>
      <td style="text-align:left">string</td>
      <td style="text-align:left">
        <p>The squad that the Battlesnake belongs to. Used to identify squad members
          in Squad Mode games.</p>
        <p><em>Example: &quot;1&quot;</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>

### Board

The game board is represented by a standard 2D grid, oriented with \(0,0\) in the bottom left. The Y-Axis is positive in the up direction, and X-Axis is positive to the right. Coordinates begin at zero, such that a board that is 11x11 will have coordinates ranging from \[0, 10\].

![Battlesnake Coordinate System](../../.gitbook/assets/10-full.png)

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
  "hazards": [
    {"x": 0, "y": 0}, 
    {"x": 0, "y": 1}, 
    {"x": 0, "y": 2}
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
        <p>The number of rows in the y-axis of the game board.</p>
        <p><em>Example: 11</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>width</b>
      </td>
      <td style="text-align:left">integer</td>
      <td style="text-align:left">
        <p>The number of columns in the x-axis of the game board.</p>
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
      <td style="text-align:left"><b>hazards</b>
      </td>
      <td style="text-align:left">array</td>
      <td style="text-align:left">
        <p>Array of coordinates representing hazardous locations on the game board.
          These will only appear in some game modes.</p>
        <p><em>Example: [{&quot;x&quot;: 0, &quot;y&quot;: 0}, ..., {&quot;x&quot;: 0, &quot;y&quot;: 1}]</em>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>snakes</b>
      </td>
      <td style="text-align:left">array</td>
      <td style="text-align:left">
        <p>Array of <a href="./#battlesnake">Battlesnake Objects</a> representing all
          Battlesnakes remaining on the game board (including yourself if you haven&apos;t
          been eliminated).</p>
        <p><em>Example: [{&quot;id&quot;: &quot;snake-one&quot;, ...}, ...]</em>
        </p>
      </td>
    </tr>
  </tbody>
</table>


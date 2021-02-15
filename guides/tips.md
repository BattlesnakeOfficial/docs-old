---
description: A collection of tips for developing your best Battlesnake.
---

# Developer Tips

These tips have been suggested and collected by the community over the years. Hopefully, they'll be helpful to new Battlesnake developers playing the game for the first time!

## Names are Important!

Be creative with your Battlesnake name and description. Names like _"test"_ or _"snek-1"_ are super popular and are easy to confuse with other developer's Battlesnakes. If you really want your Battlesnake to stand out during competitions, best to give it a creative and unique name.

{% hint style="info" %}
**Tip:** The best Battlesnake names are fun, creative, and also abide by our [Code of Conduct](https://play.battlesnake.com/about/conduct/). Battlesnake and Team names in violation of our Code of Conduct will not be tolerated.
{% endhint %}

## Consider Concurrency and Use Game IDs

Web development often means handling multiple requests concurrently, and Battlesnake is no different. It's quite likely your Battlesnake will be playing multiple games at once, and you should develop your web server with that in mind.

Start thinking about this early, and use the Game ID in the [Start](../references/api.md#start), [Move](../references/api.md#move), and [End](../references/api.md#end) requests to keep your Battlesnake's brain organized.

{% hint style="info" %}
**Tip:** Not all web servers are built for handling multiple requests concurrently. Most of the [Starter Projects](../references/starter-projects.md) are setup for concurrency by default.
{% endhint %}

## Keep Your Battlesnake Server Running

Some hosting services like [Heroku](https://www.heroku.com/), [Repl.it](https://repl.it), and even [AWS](https://aws.amazon.com/) will de-provision or turn off servers when they're at low usage. For example, free Heroku apps will sleep automatically after 30 minutes of inactivity.

Think about strategies you can deploy to make sure your Battlesnake is awake and running at full speed when you need it most.

{% hint style="info" %}
**Tip:** This problem is relevant to all web development, not just Battlesnake. We encourage you to explore ways software developers solve this outside of Battlesnake too.
{% endhint %}

## Don't Take Too Long to Respond

The Battlesnake game engine gives each Battlesnake a limited amount of time to respond to API requests - if your Battlesnake takes too long, it could be disqualified from games or the engine could make moves on its behalf.

The amount of time you have to respond is provided in each API request sent. In most cases, it defaults to 500ms, but this value can change in different game modes and tournament divisions.

For most Battlesnake developers this won't be a problem. However top competitors will optimize their Battlesnakes to use as much compute time as possible.

{% hint style="info" %}
**Tip:** Response time includes round-trip latency. The Battlesnake game engine timeouts also include the time it takes to send the request to your server and receive the response back. Consider this extra response time when optimizing your Battlesnake.
{% endhint %}

## Testing Your Battlesnake Locally

All Battlesnake game logic is [open source](https://github.com/BattlesnakeOfficial/rules) and available for personal use. If you'd like to run games locally using your own development environment, there's an included CLI.

Install the [Battlesnake Rules CLI](https://github.com/BattlesnakeOfficial/rules/tree/main/cli) to get started.

{% hint style="info" %}
**Tip:** Running games locally can speed up your development cycles significantly, but can also be more complex than using the Battlesnake platform.
{% endhint %}


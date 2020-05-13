---
description: A guide to creating your first Battlesnake
---

# Getting Started

### What is Battlesnake?

A Battlesnake is a programmed web server that implements the [Battlesnake API](https://docs.battlesnake.com/snake-api) to play the game snake against other Battlesnakes. When a game is running, the Battlesnake Game Engine will make HTTP requests to your server, sending you game information and asking for your next move.

### Step 1: Build Your Battlesnake

Select a technology you want to use to program your Battlesnake server. Anything that can process a web request and be deployed to the internet will work. There are several well documented Starter Snakes Projects that can be used as a base if you don’t want to start from scratch. Each is built with a popular programming language and web application framework.

A functional Battlesnake server must support 4 endpoints that will be called at different times during each Battlesnake game.

#### GET /ping

The engine is asking your Battlesnake if it is alive and functional

#### POST /start

Notifies your Battlesnake that it is participating in a new game.

#### POST /move

Called once per turn of each game, providing important information about the game board and asking your Battlesnake for its next move.

#### POST /end

Notifies your Battlesnake that the game is now over and which Battlesnake has won.

Each endpoint will be sent a JSON data blob by the Game Engine and your server must respond with a HTTP 200 OK status code and an appropriate JSON response. The protocol for these requests and responses are defined in detail in the Battlesnake API Reference.

{% hint style="info" %}
**Snake Wisdom: Concurrent Games**

Your Battlesnake is a live web service and could be playing multiple games at the same time. The /start, /move and /end requests will all contain a Game ID that uniquely identifies which game the request is for. You should develop your snake to handle requests from different games at the same time.
{% endhint %}

### Step 2: Deploy Your Battlesnake

Before your Battlesnake can enter games and do battle, it must be deployed to a publicly accessible web server. This can be done using a cloud hosting provider such as [Heroku](https://www.heroku.com/) or [Amazon Web Services](https://aws.amazon.com/). Many of these services provide a free tier for new accounts.

Most of the [Starter Snake Projects](https://docs.battlesnake.com/starter-snakes) have instructions for deploying quickly to Heroku, which is a great option if you’re new to web development or uncomfortable deploying code to a live server on your own.

{% hint style="info" %}
**Snake Wisdom: Don't Take Too Long**

The Game Engine gives snakes 500ms to respond to a `/move` request, including any network time. If your snake does not respond in time, the engine will reuse the move from the previous turn.
{% endhint %}

### Step 3: Register Your Battlesnake

Once your Battlesnake is operational, it needs to be registered on the Battlesnake website. Click on the button below to setup a new snake.

[Click here to Register a new Battlesnake.](https://play.battlesnake.com/account/snakes/create/)

{% hint style="info" %}
**Snake Wisdom: Names Are Important!**

Be creative with your Battlesnake name and description! Names like _test_ or _snake-1_ are easy to confuse with other developer’s Battlesnakes and fail to tell viewers anything about your Battlesnake.

That said, creativity has limits. Make sure not to violate the [Battlesnake Code of conduct](https://play.battlesnake.com/about/conduct/) with your choices or your Battlesnake may be removed.
{% endhint %}

### Step 4: Test Your Battlesnake

You are now ready to test your snake against others in live games. Creating new Battlesnake games is super easy, here are some steps to get you started:

* Go to your profile page on the Battlesnake website
* Click on the **Play Game** button - You will see a game creation form with your Battlesnake preselected.
* Use the **Add a Random Snake** button to add a challenger.
* Click on **Start Game** button to start the game!

You will be rewarded with a view of the board that includes your Battlesnake and whichever random challenger you were paired up with. Click on the Play button at the bottom of the board to start the match and see who wins!


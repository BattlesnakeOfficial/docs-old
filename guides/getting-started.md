---
description: A guide to creating and deploying your first Battlesnake.
---

# Quick Start Coding Guide

**Battlesnake is an autonomous survival game.** Each Battlesnake is controlled autonomously by a live web server and moves independently attempting to find food, avoid other Battlesnakes, and stay alive as long as possible.

Anyone can compete and win, and success at the highest level requires creativity, unique strategies, and excellent programming.

## How does it work?

Developers build and deploy a web server that implements the [Battlesnake API](../references/api.md). When a game is created,  the game engine will make HTTP requests to your Battlesnake server, sending game board information and asking for your next move. Your Battlesnake's behavior is determined by how you program it to respond to these requests. 

You can use any programming language, cloud platform, and strategy want - from simple game logic to machine learning and AI.

## Step 1: Select a Starter Project

There are several community-built and supported starter projects for most popular languages and technologies. Each one is documented with detailed development and deployment instructions.

[Start by choosing one to work with.](../references/starter-projects.md) Python, JavaScript, and Ruby are popular choices. It's possible to use most programming languages, but some will be easier than others.

{% hint style="info" %}
**Tip:** If you're unsure what language to choose, we suggest starting with [JavaScript](https://github.com/BattlesnakeOfficial/starter-snake-node) or [Python](https://github.com/BattlesnakeOfficial/starter-snake-python) as they're both widely supported and popular in the Battlesnake community.
{% endhint %}

### The Battlesnake API

The Battlesnake API consists of four commands. These commands are called at different times during each game and your response to these command controls how your Battlesnake appears and behaves on the game board.

[**Command: Get Battlesnake**](../references/api.md#undefined)  
This command is called periodically by the game engine and the Battlesnake platform. It should return information about your Battlesnake, including who created it and what it looks like.

[**Command: Start Game**](../references/api.md#start)  
This command is called once at the beginning of every game to let your Battlesnake know that a new game is about to start.

[**Command: Move**](../references/api.md#move)  
This command is called once per turn of each game, providing information about the game board to your Battlesnake and asking for its next move. Your response to this command determines how your Battlesnake behaves and will be the primary focus of your game logic programming.

{% hint style="info" %}
**Tip:** We recommend starting out by hardcoding your Battlesnake to move in a specific direction, such as "left" or "right". This will let you make sure your server is working correctly before implementing more complex logic.
{% endhint %}

[**Command: End Game**](../references/api.md#end)  
This command is called once after each game has completed to let your Battlesnake know that the game is over.

**For details on how each command works**, we recommend reading through the code in the [Starter Projects](../references/starter-projects.md) and the [Battlesnake API Reference](../references/api.md).

{% page-ref page="../references/api.md" %}

## Step 2: Deploy Your Battlesnake

Once you've selected a starter project and gone through the code, it must be deployed to a publicly accessible web server. This can be done using a cloud hosting provider such as [Heroku](https://www.heroku.com/), [Amazon Web Services](https://aws.amazon.com/), or even [Repl.it](https://repl.it). Many of these services provide a free tier for new accounts.

Most of the [Starter Projects](https://docs.battlesnake.com/starter-snakes) have instructions for using [Heroku](https://heroku.com) or [Repl.it](https://repl.it), which are great options if you are new to web development or uncomfortable deploying code to a live server on your own.

Successfully deploying your Battlesnake should provide you with a unique URL. Opening that URL in a browser should show your Battlesnake in action!

{% code title="https://your-battlesnake-server.com" %}
```text
{"apiversion": "1", "author": "BattlesnakeOfficial", "head": "default", "tail": "default", "color": "#888888"}
```
{% endcode %}

## Step 3: Register Your Battlesnake

Once your Battlesnake has a working URL, you can register it on the Battlesnake website and start playing games. Click on the button below to setup a new snake.

[Click here to Register a new Battlesnake in your account.](https://play.battlesnake.com/account/snakes/create/)

If everything is setup correctly, your Battlesnake should show as operational with the appropriate color, head, and tail. Some additional information will be displayed about the latency of communication between the game engine and your Battlesnake server.

## Step 4: Create Your First Game

You are now ready to test your Battlesnake in live games! Here's how to create a new game:

* Go to [**play.battlesnake.com**](https://play.battlesnake.com)
* From the navigation menu, choose [**Create Game**](https://play.battlesnake.com/account/games/create/)

![Form for creating a new Battlesnake game](../.gitbook/assets/getting-started-create-game.png)

* Click the ➕ next to your Battlesnake to add it to the game

{% hint style="info" %}
**Tip:** You can also add other Battlesnake to your game, either by searching for them by name or using the 'Add a Random Battlesnake' button.
{% endhint %}

* Click on **Start Game** button to start the game

You will be rewarded with a view of the game board that includes your Battlesnake and any other Battlesnakes you added to the game. Click **Play** to start the game and watch your Battlesnake in action.

![A fresh Battlesnake game with your first Battlesnake ready to go](../.gitbook/assets/getting-started-gameboard.png)

## Next Steps

**Congratulations, you've built and deployed your first Battlesnake!** 🎊\*\*\*\*

At this point you're ready to start making your Battlesnake smarter and more competitive. Typical Battlesnake development looks like:

1. Decide how you want to your Battlesnake to move in a specific situation
2. Program your Move Command accordingly
3. Deploy your changes to your web server
4. Create new games and test your new behaviour
5. Repeat until undefeated

We suggest reading the [Battlesnake Game Rules](../references/rules.md) and [Tips & Tricks](tips.md) guide to make sure you understand how to program your Battlesnake to win the most games possible.

{% page-ref page="../references/rules.md" %}

{% page-ref page="tips.md" %}

You can also check out the [Battlesnake Awesome List](https://github.com/xtagon/awesome-battlesnake), built by [Xtagon](https://play.battlesnake.com/u/xtagon/) and maintained by the community for great Battlesnake resources. Anyone may [contribute](https://github.com/xtagon/awesome-battlesnake/blob/master/CONTRIBUTING.md), so if you know of any interesting resources or wish to share your own creations, [open a pull request](https://github.com/xtagon/awesome-battlesnake/pulls).

**Good luck, and happy programming!**


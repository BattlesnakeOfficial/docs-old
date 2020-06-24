---
description: Questions frequently asked by Battlesnake developers
---

# FAQ

## Do I need to know how to program to play Battlesnake?

Battlesnake is best for those with beginner level programming skills and above. You'll have to know the basics of at least one popular programming language to get started.

If you're brand new to programming and want to start learning - awesome, we're happy you're here! We're constantly working on ways to help you get started. In the meantime, you might want to get started with some online programming courses and tutorials to get the basics down.

## Is Battlesnake only for Machine Learning and Artificial Intelligence?

You can truly use any technology you want to power your Battlesnake! It doesn't have to be machine learning or artificial intelligence - in fact, many developers have great success writing simple programs and decision trees that employ specific and creative strategies.

We suggest you start with technologies you're comfortable with and expand to include new things you want to learn.

## What cloud provider and region should I use?

You can be successful with almost any cloud provider, hosted anywhere around the world. Your cloud provider choice has no impact on your ability to play the game and we encourage you to explore and learn new things.

If you happen to be competing at the highest level and are worried about optimizing location and round-trip latency, the game engine is currently hosted in AWS US-WEST-2. It's possible but unlikely this will change in the future.

## How does food appear on the board?

The algorithm used to generate food is very simple. On each turn the game engine decides how much food to create and where to place it according to the following pseudocode.

{% code title="food-algorithm.pseudo" %}
```python
chance_of_food_appearing = 15%
if no food on game board:
    chance_of_food_appearing = 100%

if random(chance_of_food_appearing):
    # create one food on random empty square    
```
{% endcode %}

[This algorithm is open source](https://github.com/BattlesnakeOfficial/rules), and we encourage you to view the code directly.

## How are Battlesnakes ranked in Arenas?

Battlesnake Arenas use a nearly vanilla implementation of [Microsoft TrueSkill](https://www.microsoft.com/en-us/research/project/trueskill-ranking-system/) for ranking and matchmaking. The only customizations we've made are to implement a lower-bound on sigma values, to allow top-tier snakes with lots of games to still be dethroned, and we disallow ratings below zero to avoid extreme negative ratings on non-functional Battlesnakes.

## How do I organize a Battlesnake Event?

Go to our [Organizers](https://play.battlesnake.com/organizers/) page for information on how to get started running your own Battlesnake event.


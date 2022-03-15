---
description: Last updated March 2020
---

# Game Modes

Battlesnake has several game modes all built on the same foundational [game rules.](rules.md) All game modes and are available for casual play and may appear in competitions. In the API, the game mode is defined as the _ruleset_ on the [Game Object.](api/#game)

To play a specific mode, select the game mode at the top of the [Play Game](https://play.battlesnake.com/account/games/create/) page.

![Game modes available to play](<../.gitbook/assets/Screen Shot 2022-01-27 at 11.16.22 AM.png>)

## Standard

![Example Standard Game with four Battlesnakes](../.gitbook/assets/standard\_game.png)

A Standard Game is the original Battlesnake following the [game rules](rules.md) without modification.

Note that within a Standard Game the number of Battlesnake in the game can vary, and winning strategies for 1v1 games can be different than strategies for four or eight Battlesnakes.

There is a special type of standard game called 'solo', which consists of a (usually) standard game where your Battlesnake is the only Battlesnake on the board. This appears in manually created solo games and in many challenges.

## Royale

![Example Royale Game with Hazard Sauce on three sides](../.gitbook/assets/royale\_game.png)

In a Royale Game, a new danger is introduced, commonly called 'Hazard Sauce'. The Hazard Sauce slowly enters on a random edge of the board consuming an entire row or column every few turns, shrinking the 'safe' zone. If the head of a Battlesnake is within the Hazard Sauce after it moves, its health points will more rapidly decline, losing 16 health each turn. Food can and will spawn both inside and outside of the Hazard Sauce. If a snake consumes a food on a hazardous square, the hazard will not affect its health on that turn, and its health will be restored to full (100). The default hazard damage is 15, which currently adds to the normal 1 health damage per turn.

Specific scenarios and how hazards take effect:

| Scenario                                                        | Health Effect                                                                                                                                                                             |
| --------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Snake moves from empty square to empty square                   | -1                                                                                                                                                                                        |
| Snake moves from empty square to hazard square                  | -16                                                                                                                                                                                       |
| Snake moves from hazard square to empty square                  | -1                                                                                                                                                                                        |
| Snake moves from hazard square to hazard square                 | -16                                                                                                                                                                                       |
| Snake moves to hazard square also containing food               | Restored to 100                                                                                                                                                                           |
| Hazard square spawns on a snake's head at the start of the turn | <p>No effect. </p><p></p><p>Hazard damage is only applied in squares that appeared on the previous turn. The snake will have an opportunity to leave the square before taking damage.</p> |

The location of hazardous squares are found in the API on the [board object](api/#board) listed under `hazards`, and are visible on the board as a darker-grey square.

## Squad

![Example Squad Game with the purple squad overlapping at the head and tail](../.gitbook/assets/squads\_game.png)

Squad Games have two or more Battlesnakes operating as a team against at least one other squad. At minimum there must be two Battlesnakes per Squad, and two Squads per game. Squads can consist of the same Battlesnake multiple times, or different Battlesnakes. Squads will be automatically colour-matched, but other customizations, such as head and tail, will remain.

Battlesnakes that are part of the same squad may overlap any part of their tail or body, but not their heads. Two snakes of the same squad with their heads in the same square will result in a head-on-head collision and the elimination of the squad.

When one Battlesnake in a squad consumes food, all Battlesnakes in that squad benefit from that food, increasing their length and refilling their health. In the event that multiple Squad members consume food on the exact same turn, the entire Squad will only grow by one length. If any single Battlesnake in a squad is eliminated, the entire squad is eliminated.

## Constrictor

![Example Constrictor Game](../.gitbook/assets/constrictor\_game.png)

In Constrictor mode, Battlesnake tails are 'pinned' at their starting location. The Battlesnake grows by one length every turn automatically, and its health points do not decrease. No food is spawned on the board during a constrictor game.

## Wrapped

![Example Wrapped Game](<../.gitbook/assets/Screen Shot 2022-01-27 at 10.58.20 AM.png>)

Wrapped mode games expand the game board by removing the edges of the board and allowing snakes to wrap from one side of the board to the other. During a wrapped mode game, it is impossible for a Battlesnake to collide with the walls. While wrapped, a Battlesnake does not occupy any space outside of the board, the edges of the board are considered next to each other.

Food, hazards and Battlesnake collision rules will all apply normally as per standard rules of the game. If a Battlesnake moves to the other side of the board but that square is occupied by a Battlesnake, the collision will resolve normally.


---
description: Options for personalizing your Battlesnake's appearance
---

# Personalization Reference

This reference outlines all the available options for personalizing your Battlesnake's appearance. We periodically release new options, often linked to specific events or competitions.

## Choosing a Color

Your Battlesnake can choose any valid six-digit hex color code to represent it on the game board. This value is provided in response to the [GET /](api.md#undefined) command of the [Battlesnake API](api.md) and should be a 7 character string starting with "\#" that looks similar to "\#33CC00".

You can use an [HTML Color Picker Tool](https://www.w3schools.com/colors/colors_picker.asp) to help you find the exact color you're looking for.

#### **Some Example Battlesnake Colors**

![\#E80978](../.gitbook/assets/screenshot-2020-05-13-09.19.33.png)

![\#3E338F](../.gitbook/assets/screenshot-2020-05-13-09.19.58.png)

![\#4C89C8](../.gitbook/assets/screenshot-2020-05-13-09.20.29.png)

## Choosing a Head and Tail

Several personalization options are available for how your Battlesnake's head and tail will display on the game board. You can mix and match them however you like.

Just like [choosing a color](personalization.md#color), your head and tail are provided in response to the [GET /](api.md#undefined) command of the [Battlesnake API](api.md). Each value is a string, matching one of the available options shown below.

If an invalid value is returned \(or no value at all\) the `default` options will be displayed.

{% hint style="success" %}
**New Theme Releases**  
We regularly release new head and tail options, often as part of specific Battlesnake events and competitions.
{% endhint %}

### **Default Theme**

If your Battlesnake doesn't specify a head or tail these default options will be used.

![default](https://media.battlesnake.com/snakes/heads/default.svg)



![default](https://media.battlesnake.com/snakes/tails/default.svg)

### Stand**ard Theme**

_These were the first heads and tails ever released, as part of Battlesnake Victoria 2018. They hold a special spot in all our hearts._

#### Standard Heads

![beluga](https://media.battlesnake.com/snakes/heads/beluga.svg)

![bendr](https://media.battlesnake.com/snakes/heads/bendr.svg)

![dead](https://media.battlesnake.com/snakes/heads/dead.svg)

![evil](https://media.battlesnake.com/snakes/heads/evil.svg)

![fang](https://media.battlesnake.com/snakes/heads/fang.svg)

![pixel](https://media.battlesnake.com/snakes/heads/pixel.svg)

![safe](https://media.battlesnake.com/snakes/heads/safe.svg)

![sand-worm](https://media.battlesnake.com/snakes/heads/sand-worm.svg)

![shades](https://media.battlesnake.com/snakes/heads/shades.svg)

![silly](https://media.battlesnake.com/snakes/heads/silly.svg)

![smile](https://media.battlesnake.com/snakes/heads/smile.svg)

![tongue](https://media.battlesnake.com/snakes/heads/tongue.svg)

#### **Standard Tails**

![block-bum](https://media.battlesnake.com/snakes/tails/block-bum.svg)

![bolt](https://media.battlesnake.com/snakes/tails/bolt.svg)

![curled](https://media.battlesnake.com/snakes/tails/curled.svg)

![fat-rattle](https://media.battlesnake.com/snakes/tails/fat-rattle.svg)

![freckled](https://media.battlesnake.com/snakes/tails/freckled.svg)

![hook](https://media.battlesnake.com/snakes/tails/hook.svg)

![pixel](https://media.battlesnake.com/snakes/tails/pixel.svg)

![round-bum](https://media.battlesnake.com/snakes/tails/round-bum.svg)

![sharp](https://media.battlesnake.com/snakes/tails/sharp.svg)

![skinny](https://media.battlesnake.com/snakes/tails/skinny.svg)

![small-rattle](https://media.battlesnake.com/snakes/tails/small-rattle.svg)



### **Winter Classic 2019 Theme**

_Released for the first ever Battlesnake Winter Classic event, in November 2019._

#### Winter Classic 2019 Heads

![bwc-bonhomme](https://media.battlesnake.com/snakes/heads/bwc-bonhomme.svg)

![bwc-earmuffs](https://media.battlesnake.com/snakes/heads/bwc-earmuffs.svg)

![bwc-rudolph](https://media.battlesnake.com/snakes/heads/bwc-rudolph.svg)

![bwc-scarf](https://media.battlesnake.com/snakes/heads/bwc-scarf.svg)

![bwc-ski](https://media.battlesnake.com/snakes/heads/bwc-ski.svg)

![bwc-snow-worm](https://media.battlesnake.com/snakes/heads/bwc-snow-worm.svg)

![bwc-snowman](https://media.battlesnake.com/snakes/heads/bwc-snowman.svg)

#### Winter Classic 2019 Tails

![bwc-bonhomme](https://media.battlesnake.com/snakes/tails/bwc-bonhomme.svg)

![bwc-flake](https://media.battlesnake.com/snakes/tails/bwc-flake.svg)

![bwc-ice-skate](https://media.battlesnake.com/snakes/tails/bwc-ice-skate.svg)

![bwc-present](https://media.battlesnake.com/snakes/tails/bwc-present.svg)

### **Stay Home and Code Theme**

_Released as part of our Stay Home and Code event in April 2020, raising money for_ [_Food Banks Canada_](https://www.foodbankscanada.ca/)_._

#### Stay Home and Code Heads

![shac-caffeine](https://media.battlesnake.com/snakes/heads/shac-caffeine.svg)

![shac-gamer](https://media.battlesnake.com/snakes/heads/shac-gamer.svg)

![shac-workout](https://media.battlesnake.com/snakes/heads/shac-workout.svg)

![shac-tiger-king](https://media.battlesnake.com/snakes/heads/shac-tiger-king.svg)

#### Stay Home and Code Tails

![shac-coffee](https://media.battlesnake.com/snakes/tails/shac-coffee.svg)

![shac-mouse](https://media.battlesnake.com/snakes/tails/shac-mouse.svg)

![shac-weight](https://media.battlesnake.com/snakes/tails/shac-weight.svg)

![shac-tiger-tail](https://media.battlesnake.com/snakes/tails/shac-tiger-tail.svg)




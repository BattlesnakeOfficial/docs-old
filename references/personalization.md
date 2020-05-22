---
description: Options for personalizing your Battlesnake's appearance
---

# Personalization Reference

## Introduction

This reference outlines all the available options for personalizing your Battlesnake's appearance. We periodically release new options, often linked to specific events or competitions.

Each Battlesnake can choose a color, head, and tail to represent it on the game board. Here's an example of a full personalized Battlesnake.

{% code title="snake-personalization.json" %}
```javascript
{
	"color": "#736CCB",
	"headType": "beluga",
	"tailType": "curled"
}
```
{% endcode %}

This configuration will display your Battlesnake like this:

![](../.gitbook/assets/samplesnake.png)

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

![default head and tail](../.gitbook/assets/defaultsnake.png)

### Stand**ard Theme**

_These were the first heads and tails ever released, as part of Battlesnake Victoria 2018. They hold a special spot in all our hearts._

#### Standard Heads

![beluga, bender, dead, evil ](../.gitbook/assets/standardheads1.png)

![fang, pixel, sand-worm, safe](../.gitbook/assets/standardheads2.png)

![shades, silly, smile, tongue](../.gitbook/assets/standardheads3.png)

#### **Standard Tails**

![block-bum, bolt, curled, fat-rattle](../.gitbook/assets/standardtail1.png)

![freckle, hook, pixel, round-bum](../.gitbook/assets/standardtail2.png)

![sharp, skinny, small-rattle](../.gitbook/assets/standardtail3.png)

### **Winter Classic 2019 Theme**

_Released for the first ever Battlesnake Winter Classic event, in November 2019._

#### Winter Classic 2019 Head

![bwc-bonhomme, bwc-earmuffs, bwc-rudolph, bwc-scarf](../.gitbook/assets/winterheads2.png)

![bwc-ski, bwc-snow-worm, bwc-snowman](../.gitbook/assets/winterheads1.png)

#### Winter Classic 2019 Tails

![bwc-bonhomme, bwc-flake, bwc-ice-skate, bwc-present](../.gitbook/assets/wintertails.png)

### **Stay Home and Code Theme**

_Released as part of our Stay Home and Code event in April 2020, raising money for_ [_Food Banks Canada_](https://www.foodbankscanada.ca/)_._

#### Stay Home and Code Heads

![shac-caffeine, shac-gamer, shac-workout, shac-tiger-king](../.gitbook/assets/shacheads.png)

#### Stay Home and Code Tails

![shac-coffee, shac-mouse, shac-weight, shac-tiger-tail](../.gitbook/assets/shactails.png)


---
description: Options for personalizing your Battlesnake's appearance
---

# Personalization

This reference outlines all the available options for personalizing your Battlesnake's appearance. We periodically release new options, often linked to specific events or competitions.

## Color

Your Battlesnake can choose any valid six-digit hex color code to represent it on the game board. This value is provided in response to the [GET /](api.md#undefined) command of the [Battlesnake API](api.md) and should be a 7 character string starting with "\#" that looks similar to "\#33CC00".

You can use an [HTML Color Picker Tool](https://www.w3schools.com/colors/colors_picker.asp) to help you find the exact color you're looking for.

#### **Examples**

![\#E80978](../.gitbook/assets/screenshot-2020-05-13-09.19.33.png)

![\#3E338F](../.gitbook/assets/screenshot-2020-05-13-09.19.58.png)

![\#4C89C8](../.gitbook/assets/screenshot-2020-05-13-09.20.29.png)

## Head and Tail Themes

Several personalization options are available for how your Battlesnake's head and tail will display on the game board. You can mix and match them however you like.

Just like [choosing a color](personalization.md#color), your head and tail are provided in response to the [GET /](api.md#undefined) command of the [Battlesnake API](api.md). Each value is a string, matching one of the available options shown below. If an invalid value is returned \(or no value at all\) the `default` options will be displayed.

{% hint style="success" %}
**We periodically release new head and tail options, often connected to Battlesnake events and competitions.**
{% endhint %}

### **Standard Theme**

_These were the first heads and tails ever released, as part of Battlesnake Victoria 2018. They hold a special spot in all our hearts._

### **Winter Classic 2019 Theme**

_Released for the first ever Battlesnake Winter Classic event, in November 2019._

### **Stay Home and Code Theme**

_Released as part of our Stay Home and Code event in April 2020, raising money for_ [_Food Banks Canada_](https://www.foodbankscanada.ca/)_._


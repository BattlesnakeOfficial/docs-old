---
description: How to make your Battlesnake as unique as you!
---

# Customizing Your Battlesnake

Your Battlesnake’s appearance is decided in your response to the `/start`

Make your snake unique by assigning it a color, head, and tail in your response to the [Battlesnake API Start Request](https://docs.battlesnake.com/snake-api#tag/endpoints/paths/~1start/post). Your response can select a `headType` and `tailType` style, as well as choose a `color` for your Battlesnake.

### Example Start Request Response

```javascript
{
	"color": "#736CCB",
	"headType": "beluga",
	"tailType": "curled"
}
```

The above response will customize your Battlesnake to look like this:

![](../.gitbook/assets/screenshot-2020-05-12-09.26.53.png)

### Assigning a Color

Specify the `color` for your snake using a HEX code, such a `#736CCB`. The value you provide must be 7 characters long and begin with `#`. If you do not specify a color, specify an invalid option, a random color will be assigned.

### Choosing and Head and a Tail

Find your favorite head and tail combo from the options below and use the name in the parameters `headType` and `tailType`. Both of these values default to `regular` if not provided or not recognized.

**Note:** These heads and tails can be mixed and matched however you want. They’re arranged here by themes just for convenience.

**Standard Theme \(2019\)**

| **Tails** | Heads |
| :--- | :--- |
| regular | regular |
| block-bum | beluga |
| bolt | bendr |
| curled | dead |
| fat-rattle | evil |
| freckled | fang |
| hook | pixel |
| pixel | safe |
| round-bum | sand-worm |
| sharp | shared |
| skinny | silly |
| small-rattle | smile |
|  | tongue |

**Winter Classic Theme \(2019\)**

_Released for Battlesnake Winter Classic, November 2019_

| **Tails** | Heads |
| :--- | :--- |
| bwc-bonhomme | bwc-bonhomme |
| bwc-flake | bwc-earmuffs |
| bwc-ice-skate | bwc-rudolph |
| bwc-present | bwc-scarf |
|  | bwc-ski |
|  | bwc-snow-worm |
|  | bwc-snowman |

**Stay Home and Code Theme \(2020\)**

_Released for Stay Home and Code, April 2020_

| Tails | Heads |
| :--- | :--- |
| shac-coffee | shac-caffeine |
| shac-mouse | shac-gamer |
| shac-weight | shac-workout |
| shac-tiger-tail | shac-tiger-king |


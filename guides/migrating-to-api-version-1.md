---
description: A guide to migrate a Battlesnake to the latest version of the Battlesnake API.
---

# Migrating to API Version 1

### Step 1: Implement Root Endpoint

The old `POST /ping` endpoint is now deprecated and can be removed from your Battlesnake.  Instead, Battlesnakes must implement a new `GET /` endpoint that will return metadata about the Battlesnake. This is now how snakes can be customized and where they will will identify their supported API version.  

```text
{
    "apiversion": "1",
    "author" : "my_user_name",
    "color": "#888888",
    "head" : "default",
    "tail": "default"
}
```

### Step 2: Update /Start Endpoint

Any customization data in the `POST /start` endpoint is ignored by the game engine for API Version 1 Battlesnakes. You can remove any payload your are currently sending in response to a the `/start`  request. 

### Step 2: Update Coordinate System to Invert Y-Axis

Battlesnakes that implement the API Version 1 will receive the board data with a coordinate system origin \(0,0\) located in the bottom left corner of the board. In API Version 0, the coordinate system origin was in the top left corner of the board. You will either need to invert your logic with respect to the y-axis or your snake may move in unexpected ways. 

![API Version 1 Coordinate System](../.gitbook/assets/11-scale%20%281%29.png)



### Step 3: Refresh Your Battlesnake

Once your Battlesnake code is updated and deployed, go to [play.battlesnake.com](https://play.battlesnake.com/me) and use the _Refresh_  button to update your Battlesnake's metadata and upgrade it to API version 1. 

![](../.gitbook/assets/screen-shot-2020-08-24-at-11.28.17-am.png)

If you have implemented your index command correctly, you should immediately see your Battlesnake appear along with the `API v1` tag and a `Latency` tag that show the ping time of your snake.


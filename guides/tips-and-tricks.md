# Tips & Tricks

Choose names wisely!

Be prepared to play multiple games at once.

Heroku keep-alive.

Use Game ID to play multiple games at once.



{% hint style="info" %}
**Snake Wisdom: Names Are Important!**

Be creative with your Battlesnake name and description! Names like _test_ or _snake-1_ are easy to confuse with other developer’s Battlesnakes and fail to tell viewers anything about your Battlesnake.

That said, creativity has limits. Make sure not to violate the [Battlesnake Code of conduct](https://play.battlesnake.com/about/conduct/) with your choices or your Battlesnake may be removed.
{% endhint %}



{% hint style="info" %}
**Snake Wisdom: Don't Take Too Long**

The Game Engine gives snakes 500ms to respond to a `/move` request, including any network time. If your snake does not respond in time, the engine will reuse the move from the previous turn.
{% endhint %}



{% hint style="info" %}
**Snake Wisdom: Concurrent Games**

Your Battlesnake is a live web service and could be playing multiple games at the same time. The /start, /move and /end requests will all contain a Game ID that uniquely identifies which game the request is for. You should develop your snake to handle requests from different games at the same time.
{% endhint %}




---
description: Tips and common patterns for hosting your Battlesnake
---

# Hosting Suggestions

Battlesnakes must be deployed to a publicly accessible web server so they can interact with the Battlesnake Game Engine. 

![The Game Engine makes API calls to each Battlesnake, rendering the results on the Game Board](../.gitbook/assets/simple_server_diagram.png)

Most of the [Starter Projects](https://docs.battlesnake.com/starter-snakes) have instructions for using [Heroku](https://heroku.com) or [Replit](https://replit.com/), which are great options if you are new to web development or uncomfortable deploying code to a live server on your own.

Successfully deploying your Battlesnake should provide you with a unique URL. Opening that URL in a browser should show your Battlesnake in action!

{% code title="https://your-battlesnake-server.com" %}
```text
{"apiversion": "1", "author": "BattlesnakeOfficial", "head": "default", "tail": "default", "color": "#888888"}
```
{% endcode %}

There are a number of online hosting solutions that can be used with your Battlesnake. Many of these services provide a free tier for new accounts. Some popular ones in the Battlesnake community include:

### Replit

**Website**: [Replit](https://replit.com/)

* **Advantages**
  * Handles both IDE and hosting - see the [Quick Start Coding Guide](../guides/getting-started.md) for detailed instructions.
  * Everything is in your web browser - no need to install software or run anything locally.
  * Free tier is good for getting started.
* **Gotchas**
  * Might not have the most up-to-date version of your preferred programming language.
  * For speed and by default, your Replit instance will be run close to where you are, geographically. This is an advantage when using your IDE \(quick when you are writing code\) but may result in [high-latency](api/#request-timeouts), and in the worst case, timeouts, for your Battlesnake if you and your server are located in a country far-away from where the [Battlesnake servers](../faq.md#what-cloud-provider-and-region-should-i-use) are.
* **You should probably use Replit if...**
  * You are just getting started and want to test out Battlesnake without too much commitment or setup.
  * You don't want to have to manage your own hosting yet.

### Heroku

**Website**: [Heroku](https://www.heroku.com/)

* **Advantages**
  * Handles the hosting for you.
  * Great learning opportunity - chance to start experimenting with hosting without having to do everything by yourself.
  * Free tier provides up to 1,000 dyno hours/month.
* **Gotchas**
  * Free tier is _not quite enough_ hours to run for an entire [League Event](../guides/quick-start-league-guide.md), and your Battlesnake may stop if you run out of hours.
* **You should probably use Heroku if...**
  * You want full control over your IDE and local development environment.
  * You don't want to have to manage your own hosting yet.

### AWS

**Website**: [Amazon Web Services](https://aws.amazon.com/) 

* **Advantages**
  * Handles hosting, a more advanced choice.
  * Great learning opportunity to learn a variety of professional Ops/Devops skills and practices.
  * If you have never had an AWS account before, there is a program to get [1 year free T2 instance](https://aws.amazon.com/ec2/instance-types/t2/).
* **Gotchas**
  * Besides the free T2 promotion, paid option only.
  * If you use the free T2 promotion, it is important to remember to turn it off at the end of your year unless you want to be billed!
* **You should probably use AWS if...**
  * You want full control over the hosting and deployment of your app.
  * It is important to you to host your server very close to the [Battlesnake servers](../faq.md#what-cloud-provider-and-region-should-i-use).
  * You are already experienced or want to become more experienced with using AWS.

### 


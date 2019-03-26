---
layout: post
title: IGN Submission Thought Process
---

_This post addresses the thought process for questions 3 and questions 4_.

### Question 3
After a hard fought battle with a particularly tough Werewolf, renowned Witcher Geralt of Rivia is in need of some new armor. Fortunately, there was a bounty for the recently defeated beast, and for his triumph Geralt has received a good bit of coin ( called Crowns ). Traveling to a nearby armorer, Geralt is faced with more options than he is used to. Given his funds, the Witcher needs to purchase an armor set with the highest possible total armor value.

Create a program that will determine the armor set of the highest value based on Geralt’s available currency ( Crowns ). An armor set requires one piece of armor of each type (Chest, Leggings, Helmet, Boots) as well as an extra piece that can be of any type.

* 300 Crowns Available
* You must be able to afford the total price of your armor set given your available Crowns
* Each piece of armor contains a type, name, price, and armor value
* Remember, an armor set requires one piece of armor of each type (Chest, Leggings, Helmet, Boots) as well as an extra piece that can be of any type
* Inventory in Armorer’s shop [provided](https://s3.amazonaws.com/o.www.ign.com/code-foo/2019/static/Witcher+Inventory+(1).pdf)
* Display the final answer.
* Explain how you implemented the solution. Is your solution successful with other inventories?

When I first looked at this problem, I immediately thought for better or worse, that this was a recursive back-tracking problem.

That notion was obviously wrong, given that its not a single variable problem. We're attempting to maximize a variable `total_av`, while keeping another variable `cost` under a threshold. You can see this in the question file where I write that I was concerned about the "edge case" of having an extra piece that provides more armor value for the buck, pushing some other piece out of the equation.

In other words, this is an optimization problem, one that can be described through the application of linear programming.

I chose to use python to solve this exercise, due to the fact that python has really _really_ simple file i/o and handling and was something I was already really familiar with.

I wrote the file i/o and parsing stuff roughly two weeks ago, at like 2am in the morning (That's when I started the application)

Of course, being the person I am, I managed to not get work done for the next week (in my defense, it was midterms).

The next week was spring break, and given that I had made little to no progress on question 4 at this point, I devoted my time to addressing that question instead.

The amount of work I did on question 4 by day kinda looked like this:

&lt;INSERT HUMOROUS PLOT.LY EXPONENTIAL GRAPH&gt;

Before I knew it, it was 12am monday march 25th EST (thank god for the 3 hour difference) and I still had not picked up on where I had left off on question 3.

This obviously led to some very hacky code with variables and stuff littered around everywhere.

Despite this, I still think my approach kinda makes sense, so I'll explain what I did.

I knew that given the time constraints, the most time-efficient (for me) approach was brute-force (obviously not the most time-efficient in general).

After opening the file, I put each category into its own list, and made a list to contain all of these lists. The last list, the list for the extra piece, would contain all the armor pieces.

I would go through all the combinations to meet the constraints recursively and remove the piece picked from the last list, in order to avoid it from being picked again.

I chose to have inside this 2D list, a dictionary with the key being the armor name, and its value being another list containing two elements, the armor value and cost.

I felt this made for easier data retrieval.

The recursive function would take five parameters: `armorIndex`, `cost`, `av`, `path`, and `arm4`. ArmorIndex is the index into the  megalist; With it, I can increment to traverse across each individual category of armor that Geralt needs. `cost` and `av` were needed in order to mutate them in the function definition.

`path` is a list and is needed in order to keep track of the name choices (the different paths). If the armor piece is selected, it's name is added to the path.

Finally `arm4` is needed because recursively, I believe (I could be wrong) python's nature of shallow copying and inherent memory referencing, makes it so that I can't mutate into arm[4] (indexing the megalist) directly and just pass `arm` into the params, since only arm[4]'s reference was mutated, instead of the entirety of `arm`.

The program computes each `PATH`, and if the `PATH` meets the constraints and has a higher `total_av` that the global `total_av`, the global `PATH` is changed to that `PATH`.

<hr>

### Question 4

Question 4 presented several options. I could choose to build a frontend application (React and mobile optimization), I could choose to build a backend mysql service (parse and clean the DB, and build api for it), I could choose to build an app (what I did), or build a fullstack chat application (sockets, networking, pretty much all of what was mentioned above, unless you're using a DBaaS or cloud storage like Cloud Firestore).

I ruled out the frontend app since I suck at responsive screen designing and have not used React (or Vue) in any mid to large project capacity. My redux skills are still next to none, and a job application isn't the best idea for complete experimentation.

I pondered the mysql service, since I consider myself more of a backend developer (mostly program in python and java, with some rust). The problem here was that my sql knowledge was mostly postgresql. sqlalchemy and ORMs make it relatively the same, but I just didn't feel that into this one.

I considered the fullstack application, but felt like it was the most work out of all of them.

I settled on the app, because I had a bit of flutter experience, building projects with flutter at [hackBU](http://hackbu.org/2019s/) and [treehacks](https://www.treehacks.com/). There was a big problem though. The IGN Code Foo project [page](https://www.ign.com/code-foo/2019) stated that all questions had to be answered using a combination of the following: Java, Scala, PHP, Ruby, Python, Swift, Kotlin, Objective-C, or JavaScript. Dart isn't mentioned anywhere on that list.

I got an email confirmation that using flutter was ok, and proceeded to start my application.

To start a flutter project, you first need to have flutter. I installed flutter via the instructions provided [here](https://flutter.dev/docs/get-started/install/linux), setting up via the vs code path.

I then proceeded to build a skeleton project with

```bash
flutter create ign_q4_app
```

I first needed to get the api data from the data source, in this case [http://ign-apis.herokuapp.com/](http://ign-apis.herokuapp.com/)

_To be continued_


---
layout: post
title: Bootstrapping Banh, a smart calendar
date: 2020-01-04 12:14 -0400
---

I’ve always felt like current productivity solutions are kinda hit and miss. There’s your standard calendar, like Google Calendar. You get a calendar that lets you schedule events at respective timeslots, in an easy to use and forthright manner.

You also have your todo lists. Todoist, Wunderlist (acquired and incorporated into Microsoft ToDo), any.do, and moo.do are all popular todo list solutions.

These tools approach the same problem from two different perspectives. This problem is how can I achieve X tasks in Y time so I can do Z?

A calendar approaches this by recognizing that many of us follow a daily, monthly, even weekly routine. It knows that these events are largely the same day to day and should really be programmed in at the beginning. This tends to be very helpful for things like classes or weekly meetings.

The todo list approaches this problem differently. The question  the todo list asks itself, is what stuff *matter*? The todo list is deliberately not large in order to enable a person to quickly scan said list and determine what item gets what priority. Things like labels to sort these items are often included in most modern todo list software. This tends to be beneficial to people who have to deal with a large amount of tasks, with varying priorities and relation.

I find that these approaches could still be improved. Now, don’t get me wrong, they’re still very useful. If they weren’t, people wouldn’t use them. I just find them to be an imperfect solution, trying to fit a square peg into a circular hole.

Let’s do this through the examination of the CRUD associated with both a calendar and a todo list. CRUD stands for Create, Read, Update, and Delete and is a term that is often associated  with computer science and its related data structures. The use of a specific data structure carries with it, a unique set of CRUD operations, which fit different use cases. For example, a company like Netflix would probably care about having high Read and Update for its movie library given that its library is constantly changing and subscribers expect fast load times.

A calendar like GCal has slow create, due to the fact that it requires a high degree of user interaction. The user needs to create the event, its description, and its formalities. A calendar has very fast read, however, especially given that almost all of them automate their push notifications. Update is slow because a time has to be picked out, requiring the status of the event to be changed. Delete is moderate, given that it is fast for singular events, but not so much for events that have unique time schedules and recurrences.

A todo list has fast create, read, update, and delete.

The CRUD for the todo list is ideal. It would seem that people should rely on todo lists over calendars any day, every time. Yet we know this is not the case.

Calendars maintain an edge because they understand human activity is often routine (a sparse graph over a dense graph). They don’t have the ideal CRUD though, which is the area where they can be improved.

## Introducing banh

What if we combined the best features of the two? That’s how I arrived at banh, what I deem a smart calendar. Banh seeks to bridge several gaps, namely:

1. Calendar rigidity

The reason for why calendars have such a high update is the event’s association to a given timeslot. Banh introduces a new feature, called the *event library* which contains these events, irrespective of when they happen or what slot time they occur at. This means that the create operation takes a little longer, since it means adding the event to the event library, before adding it to the calendar, but it significantly offloads   rescheduling. This is helpful for dealing with real life meetings and appointments, which are often rescheduled.

Another upshot of this approach is that with this increased flexibility, you can schedule in things that better meet what you hope to achieve, bringing up the next point.

2.&nbsp;Goal oriented

Let’s be real. Most of you have goals. If you’re here, you’re frustrated about your current productivity, or interested in improving it. Tasks should be a mean towards achieving your goals, whether it’s getting a promotion, being a great dad, or staying fit. Banh lets you dump your goals in and devise a series of rules to better achieve these goals.

3.&nbsp;Context aware

I’m a New Yorker and have experienced my fair share of cold weather up here. This weather can directly impact my plans for things like exercise, as I try to bike to and from school twice a week. Banh will have a robust API to integrate the surrounding context, whether it be the weather, program closings, etc. such that you can better achieve your goals.

4.&nbsp;Voice first

I’m skeptical of voice tech. I don’t really use Google assistant and from what I know, voice tech is really limited to Alexa and some basic commands.

I think a large reason behind this lack of use of voice tech is  that there is no 10x bonus. A product generally has to be at least 10x better than an established competitor in order to achieve market traction. Why would someone bother to use Google Assistant to search for something when they could use Google itself? Is tapping the Assistant button and speaking the words any better than tapping the search button and typing them? I think voice tech fares much better when you can say

> banh reschedule meeting with Alex from today to tomorrow at 9am.

Banh will integrate voice when the MVP is firmly established.

5.&nbsp;Suggestions

I still use todo lists right now. One of my problems with todo lists is when I have so much on my plate that when I get something with such low priority, I simply don’t assign it a priority or due date, and it never gets done. I never get reminded that the activity exists and needs to be done. Banh will have reminders and suggestions for certain events to be done earlier (flexible class), depending on whether a slot is open.

There are definitely times when I am more focused and productive and there are other times when I’m not so much. Suggestions help to alleviate and prevent the latter from affecting goal-achieving.

6.&nbsp;Stats

Banh will have a robust stats page, designed to help you make the most of the data presented, to better achieve your goals.

7.&nbsp;Ethical

*Your data is your data.* I strongly believe in privacy and not making money from harvesting your data. Your app data will not be shared with third parties.

I’m currently relying on Mailchimp for audience building. I may change that soon.

I reserve the right to use Google Analytics (and you reserve the right to use an adblocker and prevent all that tracking stuff!). I promise I’ll switch to a more private solution such as Fathom or Matomo when I reach a decent level of profitability.

Transparency is also a key for me, given that we live in an age of misinformation. Banh will be an open startup, once I can get that apparatus going.

If you’d like to use banh once it launches, I’d appreciate it if you signed up at [https://banh.app](banh.app). You’ve already read this far! :)
---
title: 02 Celonis Foundations
author: JUNG YoungKyun
date: 2023-03-28
category: 37 celonis
layout: post
---

# What is an Event Log?

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fill,w_750,h_361/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/iyxeuk0wn61i-Artboard3800x385.png)

Video | 3min

Check out the foundations of our process mining technology.
    
Event Logs are the foundation of our technology. They structure the data and prepare it to be analyzed with Celonis. Watch this video to learn what Event Logs contain, and why they are crucial for Process Mining.



## What is an Event Log? Intro & example - Transcript (00:00 - 01:05)
Purchasing a gift on Amazon, ordering dinner on Fedora, or driving processes forward at work. We already mentioned that our everyday lives are full of activities that leave digital footprints.
Let's take a closer look at these digital footprints to understand what they consist of and how you need to structure them to derive a story out of your data.

Let me give you an example.
Imagine you were ordering dinner online as mentioned in the beginning. Your dinner order will have a particular order number to which all related activities are assigned.

The activities that take place are the selection of items in a menu, the payment, the preparation of the meal, the deliverer picking up the meal, and finally the delivery arriving at your doorstep.

Each of these activities leaves a digital footprint with a timestamp indicating precisely when each activity took place. This is all the information needed to create an event log so that we can start process mining.
This is quite a simple concept.

## What is an Event Log? Event Log table - Transcript (01:05 - 02:31)
The event log is a table with three columns containing all the information from our example.

The order number, showing us which activities were performed for the same dinner order.
The activities, telling us the actual activity names.
And the timestamps, revealing when each activity took place.

Still hungry, of course. The event log could contain several orders. In fact, the more orders you have in your event log, the better the stories and insights you can extract out of it. However, it is crucial that every order has a unique order number. After all, no one likes a mixed up food delivery. A unique identifier makes it possible to distinguish between different orders and correctly assign the activities and timestamps.

In the event log, we call such a unique identifier a case ID. The case ID is a reference number to document all activities and timestamps that are directly related to each case. The order number is a great example for a case ID.

Depending on the process that you want to analyze, a case ID can also be a service ticket number and invoice number or any further kind of identifiers.

Now we know what an event log is, with a case ID activity and timestamp. We have all the necessary information at hand to analyze data with Celonis process mining.

# Celonis Kickstarter

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fill,w_750,h_361/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/lcz5jj79c4m3-course_Kickstarter-2_catalog800x385.png)

Course | 1h

Get started with Celonis and our Execution Management System.

# Transform Data

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fill,w_750,h_361/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/yea1q1n7f0p3-skill-area_Conceptualize_catalogue.jpg)

Course | 1h 30min

Create transformations using Data Jobs and the Replication Cockpit.

---
title: 02 Celonis Foundations
author: JUNG YoungKyun
date: 2023-03-28
category: 37 celonis
layout: post
---

<div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="dc47834b-9c58-4dbc-8c5b-d4042d7269a9" data-share-badge-host="https://www.credly.com"></div><script type="text/javascript" async src="//cdn.credly.com/assets/utilities/embed.js"></script>

위 벳지는 수강을 완료하고 받은 뱃지입니다.

# 01 What is an Event Log?

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

## Hello!

## We're excited to have you at the Celonis Academy.

In this course, we introduce you to Celonis and our Execution Management System. You'll find out why we started and how our software breaks barriers and drives value for anyone involved in a business process. 

We want you to play an active part in this journey. So, we included hands-on exercises that let you play around with the software.

If you would like to take a break during the training, remember to close the course using the "Exit Course" button in the top left of the window first before closing your browser window. Otherwise, your progress could get lost. 

The course will take about 50 minutes to 1 hour, depending on the deep dive you choose. You can find the breakdown for each section beside the lesson title.

After you complete this course, you earn your first Celonis Digital Badge.

## Welcome to the Celonis Kickstarter [04:00]

### Hi there!

{% include youtube.html id="Bvi1R5UeQvo" %}

### Learning Objectives

Here's what you can expect to get out of this course:

1. Summarize what an Event Log is and why we need it for Process Mining.

2. Identify business use cases for Celonis.

3. Know the core components of the Celonis Execution Management System. 
    - Celonis Analyses to identify process inefficiencies.
    - Apps to take action.
    - Action Flows to automate your processes.

4. Find your Celonis fit and training courses to get started.

5. Share your first Celonis Digital Badge.

Which technology did Celonis pioneer in 2011?

- [x] Process Mining

- [ ] Execution Management System

- [ ] Task Mining

We started Celonis in 2011 and pioneered Process Mining to help you get an x-ray of the actual process flow, revealing and fixing inefficiencies, and empowering you to perform at levels you never thought possible.

In 2020, we introduced a new software category, the Execution Management System, to extend Process Mining. We wanted to go above and beyond to help you turn your process insights into real-time actions.

## What is Process Mining? [06:00]

### Get an x-ray of your business

You’ve already heard that processes often don’t run the way we designed them. Inefficiencies are everywhere: in every process, company, and industry. 

Process Mining gives you a real-time x-ray of your business processes — a living, breathing, moving picture that shows you where inefficiencies hide.

Get the first glimpse in the following video.

{% include youtube.html id="AN_Keu8mtVA" %}

Let’s focus on the x-ray. How can Celonis lift the blindfold and see how the process runs?

At the core of process mining exist event logs. `Event logs structure the digital footprints in your processes and prepare them for Celonis’ x-ray.` Data engineers usually design them for business processes. However, we also show you how you can make your own.

But first things first. The video below explains to you what an Event Log is by using an everyday example: ordering dinner online. 

{% include youtube.html id="Lh0V9KWr2Tg" %}

> You might have come across Event Logs referred to as 'Activity Table.' These terms are used synonymously, but both describe the same data structure we need for process mining.

Which three columns are mandatory for an Event Log?

- [x] Case ID

- [x] Activity

- [x] Timestamp

- [ ] Sorting

#### Advanced Event Log

Besides the three necessary columns, case ID, activity, and timestamp, you can add additional information to the event log. [VIDEO](https://academy.celonis.com/courses/add-advanced-columns-to-an-event-log)

#### Create your own Event Log

Assuming you want to create your own Event Log but don't have a source system or data set at hand. This guide helps you create your own. [GUIDE](https://academy.celonis.com/courses/how-to-create-an-event-log-from-scratch)

Event logs contain, at a minimum, three key pieces of process data for every individual event:

1. Case ID: A unique reference to each business object

2. Activity: The stage of the process the case went through

3. Timestamp: The time that that specific case went through that stage

You can add more information to increase context: think vendor details for an invoice or priority level for a service ticket.

### And what is Task Mining?

When learning about process mining, did you wonder what happens to all the additional steps that don’t happen in your transactional systems and therefore wouldn’t make it into the event log? Think of checking an email, consulting a spreadsheet, or doing research on LinkedIn. In these cases, task mining gets the job done.

Watch the video or take a special course to learn more.

#### What is Task Mining?

Watch this 4-minute video to find out. [VIDEO](https://academy.celonis.com/learn/video/what-is-task-mining)

#### I'm all in on Task Mining.

Dive right in, and take ‘Task Mining Basics’ to differentiate process and task mining, understand when it works, how to set up, configure and use it.

[TRAINING](https://academy.celonis.com/learn/course/task-mining-basics)

## What are Process Mining Use Cases? [07:00]

### Why companies need process mining
    
Now that you are familiar with the fundamental technology of process mining, let’s have a look at some concrete examples of how you can use it in your day-to-day work and on your journey toward reaching your full potential.

Process mining use cases are infinite given the technology cuts across multiple business functions and industries.  For instance, process mining can make the supply chain more resilient by eliminating inefficiencies. Process mining also has a big role to play in sustainability efforts. Common use cases include but are not limited to:

- `Process excellence`(opens in a new tab) including broad usage across companies to find and fix inefficiencies previously unseen. 

- `Supply chain transformation`(opens in a new tab), which is increasingly a boardroom issue.

- `Shared services transformation`(opens in a new tab) of central services that can evolve from cost center to an innovation hub. 

- `Systems transformation`(opens in a new tab) where process mining is used to migrate IT systems to become more agile. 

- `Sustainability`(opens in a new tab), which is an emerging space for process mining. More efficiency means more sustainability and often a lower carbon footprint.

These use cases are seen across multiple process mining customers in industries including automotive, consumer, energy, financial services, healthcare, manufacturing, professional services, retail, telco, media, and travel and transportation. 

### Process-specific use cases

There are additional benefits to process mining that are specific to the process you’re working on. Process mining helps you improve the outcomes of a specific process — whether it’s optimizing working capital in Accounts Payable or Accounts Receivable, improving close rates in Opportunity Management, or on-time delivery in Order Management, for example. 

Select the process that most resonates with you. Please note that the applicability of Celonis is not limited to these processes. These are just four example processes.

#### Meet Max, Accounts Payable Team Lead
- Goals
    - He aims to optimize cash flow, improve the on-time payment rate, and realize cash discounts. For Max, efficient and compliant invoice processing is crucial.

- Challenges
    - However, he struggles with unknown process inefficiencies, high volumes of manual work, and poor, siloed data.

- Solution
    - Celonis x-rays Max's Accounts Payable process and creates an easy-to-use analysis that provides Max with the insights he always wished to have.    
    - Just like Max, in Accounts Payable, Celonis helps you to reach your goals.    
        - Monitor DPO
        - Detect late invoices
        - Realize cash discounts
        - Prevent dunning charges
        - Identify manual entry errors or missing invoices
        - Spot maverick buying behavior
        - Benchmark across all your company codes

[Process Use Case Personas - Celonis Kickstarter.pdf](https://scorm.eu.thoughtindustries.com/content/1cc62825-20df-4077-8216-a9df1132a5ad/0a8f7e51-13c4-488c-9878-b809d97b8099/4/scormcontent/assets/nF0YWGVohCcTzaBq_iYMC81qc_2bFJjFT-Process%20Use%20Case%20Personas%20-%20Celonis%20Kickstarter.pdf)

##### We live for customer value

Listen to what our customers say about us. 

[CUSTOMER STORIES](https://www.celonis.com/customers/#stories)

##### Process Mining Guide for Dummies

Read all about process mining and more exciting use cases in our latest guide.

[EBOOK](https://www.celonis.com/ebook/process-mining-for-dummies/?utm_source=google&utm_medium=cpc&utm_campaign=evergreen&utm_content=en_process_mining_for_dummies_eta&creative=588859775462&keyword=process%20mining%20for%20dummies&matchtype=p&network=g&device=c&_bt=588859775462&_bk=process%20mining%20for%20dummies&_bm=p&_bn=g&_bg=134720944237&gclid=Cj0KCQjwgYSTBhDKARIsAB8KuktPJUW9G3Hhi1ILQEMimRxoqwPdfen1dRryP2vPyzZCvrt3XshlqXIaAqZbEALw_wcB)

Process mining is only the first step to transforming your business. Are you ready for the journey to Execution Management?

## Journey to Execution Management [06:00]

### Make a bold move

Now that you know how process mining works, it’s time to move from simply understanding processes to improving them. Once you’ve used process mining to gain visibility into a process, you can start to ask questions like:

- Where do we need to change activities or steps?

- Which activities could potentially be automated?

- Which actions will drive better outcomes?

You’ll get the most value from process mining by using it as part of a larger set of tools and initiatives to improve overall business execution. That is why we introduced the `Celonis Execution Management System (EMS).`

Our Execution Management System reveals and fixes hidden inefficiencies - fast. Imagine a large orchestra with countless musicians and instruments that represent your processes. They don’t know how to best play music together without an orchestrator. The Celonis EMS acts as your intelligent orchestrator, syncing your existing systems and technologies and providing what’s required to optimize your processes and achieve your desired business outcomes.

Here are three foundational components of the Celonis EMS:

- Real-Time Data
    - The EMS integrates data across your data across systems, desktops, documents, and event streams and gathers all the data needed to create an event log and perform an intelligent analysis.
- Process Intelligence
    - The EMS acts as a brain, x-rays all the moving parts of your people, processes, and technologies to uncover hidden inefficiencies and recommend relevant improvements.
- Targeted Action
    - The EMS empowers your teams to operate effectively and efficiently by executing recommended improvements through automation, prioritization, and task suggestions.

### Remember the dinner orders in our event log?

Let’s look at another order management example to see what makes the Celonis Execution Management System so powerful.

{% include youtube.html id="-O_K48426Bs" %}

#### Do you want to visit the Celonis EMS?

## Discover the Celonis Execution Management System [07:00]

So far, you’ve learned why we invented the Execution Management System and what its foundational components are. Let's dig a little deeper into its capabilities.

{% include youtube.html id="Ndas983p0Hw" %}

Which EMS capability helps you anticipate how changes in your processes will impact business outcomes?

- [ ] Process and Task Mining

- [x] Planning and Simulation

- [ ] Action Flow

### Execution Management in Action

Here’s how we put the EMS to work for order management.

{% include youtube.html id="o5f-dRF6kns" %}

### It's time to dive deeper

Now that you have seen how Celonis Analyses, Apps, and Action Flows help improve processes in order management, it’s your turn to decide which capability you would like to explore further.

Choose, and continue by clicking on one of the buttons below. You don't have a clear favorite? No worries, you can take them all. But to complete this course, you only need to go through 1 of the 3.

#### Analyze with Analyses

Learn how to navigate Celonis Analyses and uncover process inefficiencies.

[LET'S ANALYZE](https://scorm.eu.thoughtindustries.com/content/1cc62825-20df-4077-8216-a9df1132a5ad/0a8f7e51-13c4-488c-9878-b809d97b8099/4/scormcontent/index.html#/lessons/liEqkKhYPZD108Z9A97v2TNa9HtU3-aQ)

#### Act with Apps

Find out how Apps help you prioritize tasks and recommend actions.

[LET'S ACT](https://scorm.eu.thoughtindustries.com/content/1cc62825-20df-4077-8216-a9df1132a5ad/0a8f7e51-13c4-488c-9878-b809d97b8099/4/scormcontent/index.html#/lessons/heMtF5UaGWgml_HBkj5DVRpiqSCcCrEV)

#### Automate with Action Flows

Discover how you can automate your processes with Action Flows.

[LET'S AUTOMATE](https://scorm.eu.thoughtindustries.com/content/1cc62825-20df-4077-8216-a9df1132a5ad/0a8f7e51-13c4-488c-9878-b809d97b8099/4/scormcontent/index.html#/lessons/CK3pTi6KqQESPKWiNkzn_te2vBCK8xy9)

## Analyze with Analyses [15:00]

Before we start drilling deeper into Celonis Analyses, let’s recap what you’ve previously learned about process mining.

What’s the foundation of process mining that helps structure data and creates an end-to-end visualization of the process?

- [ ] System Log

- [ ] Transaction Log

- [x] Event Log

Aside from structuring and visualizing the data, a Celonis Analysis equips you with the tools to explore your process performance from many angles. Celonis surfaces inefficiencies and calculates the impact on your business based on standard or custom key performance indicators (KPIs).

Click on the hotspots below and learn more about the different analysis components:

[link](https://academy.celonis.com/learn/course/celonis-kickstarter/celonis-kickstarter/course-outline?client=public-panorama&page=2)

Watch the video below to understand different analysis components and use them to analyze your process. We use an order to cash process for training purposes, but you can transfer this to all other processes.

{% include youtube.html id="hd-U0Nfsf8g" %}

### Now it's your turn

We want you to get hands-on with Celonis Analysis. For training purposes, we are happy to share the analysis we've shown in the video above. Open and use the analysis to answer the quiz questions in the scenario below.

Order Management Analysis [OPEN ANALYSIS](https://content.training.celonis.cloud/package-manager/ui/public/assets/f0039180-a56c-4f08-bb42-3d3c9b048677#!/documents/f0039180-a56c-4f08-bb42-3d3c9b048677/view)

[link](https://academy.celonis.com/learn/course/celonis-kickstarter/celonis-kickstarter/course-outline?client=public-panorama&page=2)

### Can’t wait to get started with your own data?

Then, sign up for the Celonis Free Plan. Our Quickstarts help you upload and structure your own data and provide a ready-to-use analysis. Watch the video to find out more.

#### Learn more about Quickstarts

Watch the video.

[VIDEO](https://academy.celonis.com/courses/what-are-celonis-quickstarts)

#### Get started with Quickstart

Sign up for Celonis Free Plan, upload your data and analyze it for free.

[SIGN UP](https://signup.celonis.com/ui/sign-up/get-started)



# 03 Transform Data

![](https://d3i9g4671ronu3.cloudfront.net/thoughtindustries-eu/image/upload/a_exif,c_fill,w_750,h_361/v1/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/yea1q1n7f0p3-skill-area_Conceptualize_catalogue.jpg)

Course | 1h 30min

Create transformations using Data Jobs and the Replication Cockpit.

After completing this course, you will be able to:

- Choose the appropriate tool for transformations
- Set up transformations with Data Jobs and the Replication Cockpit
- Build your Activity table and other important tables using transformations
- Accelerate your work with templates
- Troubleshoot your transformations

WHAT'S INCLUDED
- Self-paced learning. Take courses at your own speed.
- Learn when it suits you with round-the-clock access.
- Get enabled fast with laser-focused, goal-based training.

## Intro

Learning Objectives

## Welcome!

Your central task in Data Integration is to build a process Data Model. To do so you first connect to systems, extract raw data, and then “transform” the extracted data.

Transforming means:

1. building one or more Activity Table(s) with all relevant process activities
2. reworking as necessary your Case Table(s) and other relevant master data tables.

Sounds cryptic? Not to worry, after this course you'll have mastered the foundations and will be able to:

- Explain what it means to transform data
- Choose the appropriate tool for transformations
- Set up transformations with Data Jobs and the Replication Cockpit
- Build your Activity table and other important tables using transformations
- Accelerate your work with templates
- Troubleshoot your transformations

Let's get started!

![](https://d3i9g4671ronu3.cloudfront.net/course-uploads/1cc62825-20df-4077-8216-a9df1132a5ad/tfygvkk3e21f-braden-collum-9HI8UJMSdZA-unsplash.jpg)

> Personal Training Environment Required
>
> This course contains hands-on exercises that require a personal EMS Training Environment, also called an "EMS Team".
>  
> Not sure if you have one? Click below and we'll either create one for you or show you how to access your existing Team if you have one. Please make sure to disable adblockers on this page if the button is not working for you.

## Overview of Transformations

Transformation Tools

## Choosing the Right Tool

Once you’ve established a connection, and set up your extractions, your next step is to transform the data with one or more of these tools:


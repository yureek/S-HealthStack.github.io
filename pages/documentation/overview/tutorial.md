---
title: Getting Started Tutorial
sidebar: doc_sidebar
permalink: tutorial.html
toc: true
---

This getting started tutorial describes the steps you need to be up and running with your own study. The best way to explain the steps is to walk through a simple example. Follow these steps to get started with Samsung Health Stack.

## Set up your environment

The stack consists of three pieces, which you install separately:

1. [Install the backend services and data engine.](../installation/installing-the-backend.md)
2. [Install the app software development kit (SDK).](..\installation\installing-the-sdk.md)
3. [Install the web portal.](..\installation\installing-the-portal.md)

## Set up a study

In this fictitious scenario, we've noticed that people with supernatural physical abilities have begun to appear all over the world. We call this phenomenon *Syndrome X*. We hypothesize that Syndrome X is related to specific vital signs and symptoms, such as heartrate, blood pressure, and headaches. So, we design a study to gather participants who have experienced extraordinary powers, ask them survey questions, and collect their vital signs and any symptoms. We've decided to call it the Mutant Gene (MG) study. We will collect vital signs using the Galaxy Watch 4 and symptoms using a participant survey.

Studies are managed from the Samsung Health Stack web portal. Follow these steps to set up managing the MG study:

1. [Create a new study](creating-a-study.md) in the web portal.

    > 
2. Invite team members to help conduct the study.
3. Assign managing roles to the team members.
4. [Create a participant survey](../study management/creating-a-survey.md).
   
    > From the **Study Management** page, click **Create survey** and enter these parameters:
    > - Title: Daily Symptom Report
    > - Question 1: How intense were your headaches yesterday?
    >   - Type: Slider scale
    >   - Scale: 0 (None) to 10 (Almost dying)
    > - Question 2: Which symptom(s) appeared yesterday?
    >   - Type: Multi-selection
    >   - Options: None, Mind reading, Laser from eyes, Shadow cloaking
5. [Schedule and publish the survey.](../study management/publishing-a-survey.md)
    > From the **Create survey** page, click **Publish** and enter these parameters:
    > - Frequency: Daily
    > - Survey occurrence: Appropriate publish time and duration. 

## Build the mobile app

For our study, participants wear the Samsung Galaxy Watch 4 and use an android mobile app to collect the data. Follow these steps to use the Samsung Health Stack app SDK to create and customize the app:

1. If you are not already familiar with developing code in Android Studio, take a look at https://developer.android.com/studio/intro.

2. In Android Studio, clone the starter app code from the https://github.com/S-HealthStack/starter-app GitHub repository.

   > git clone https://github.com/S-HealthStack/starter-app.git

3. Customize the sample code to determine participant eligibility, register participants, and conduct the study.

   1. update study name to "MG Study"

      update intro description to "???"

      add (or verify) eligibility question(s) - Galaxy Watch 4, others?

      add (or verify) data sources - heart rate, step count, sleep and blood pressure

      anything else to change for consent step?

      other?

4. Test your app in Android Studio.
   > Due to the lack of mature libraries for wearables, testing with the Android Studio emulator is quite limited. At this point in time, most of the testing need to happen in the live app.

5. Connect your app and the portal study.

   > <span style="color:red">In ???.xml, associate the API endpoint of the backend system and the app's portal ID.</span>

6. <span style="color:red">Make the app available for downloading.</span>

## Onboard the participants

The first step of onboarding is to onboard yourself to live test the app. Follow these participant onboarding steps:

1. Download the app to your phone.
2. Open the app and step through the prompts that you set up while building the app to determine eligibility, request consent, and register those who are eligible.
   <span style="color:red">*Note: we'll expand this section to match demo better when time permits...*</span>
3. If not already previously done, install the [Health Platform](https://play.google.com/store/apps/details?id=com.samsung.android.service.health&hl=en&gl=US) service app on your phone.
4. If not already previously done, <span style="color:red">pair your phone and the Samsung Galaxy Watch 4.</span>

Once you've tested the app to your satisfaction, invite prospective participants to complete the participant onboarding steps and join the study.

## Run the study to collect the data

In a real-world situation, the study would run until the scheduled end date you specified during survey. For this tutorial, have each participant (including yourself):

- Wear the watch to generate some data.
- Open the app and complete the daily survey.

- Use the app to see the data visualizations available to participants.


## Analyze the results

Now, return to the web portal to analyze the results. Results are available for each participant separately and for the study as a whole. You can:

- View various graphs.

- Run queries.
   > From the **Data Insights** page, in the **DATA QUERY** section, enter these parameters to list people who have experienced any symptoms of Syndrome X:
   > - Table: <span style="color:red">???</span>
   > - Query: <span style="color:red">???</span>
   >
   > Next, enter these parameters to compare the vital signs of those people and others:
   > - Table: <span style="color:red">???</span>
   > - Query: <span style="color:red">???</span>
   >
   > Due to the limited data sample size, you'll likely see no meaningful difference between two groups.

- Export the data for external analysis.
   > In the **Query Results** table, click **Export .csv**.

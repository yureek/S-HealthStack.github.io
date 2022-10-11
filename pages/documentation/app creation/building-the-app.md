---
title: Building the App
sidebar: doc_sidebar
permalink: building-the-app.html
toc: false

---
participants wear the Samsung Galaxy Watch 4 and use an Android mobile app to collect the data. Follow these steps to use the Samsung Health Stack app SDK to create and customize the app:

1. If you are not already familiar with developing code in Android Studio, take a look at https://developer.android.com/studio/intro.

2. In Android Studio, clone the https://github.com/S-HealthStack/starter-app GitHub repository to retrieve the app starter code.

   > git clone https://github.com/S-HealthStack/starter-app.git

3. Edit the code in the `main` branch to customize it for our study.

Mention basic pieces to include

* determine eligibility
* get informed consent
* register
* etc...

Next, we create a mobile app to enroll participants and obtain their vital signs. We can use our App SDK for this.  Many features are available with a few simple customizations. 

To perform research, researchers must have method to interact with participants.
Mobile applications on a smartphone is a good option for that, especially the case utilizing wearables.

From this step, we will present very simple method to build an app for participant using Healthcare Research SDK.

# Preliminaries

Currently, Research SDK covers only for Androids (and WearOS).
You'd be better to familiar with Android Studios.

Introductory materials for building Android apps.

* link1
* link2

# Make a `MG Marker` research app

## Downloading sample sources

Research Hub provides sample android application sources using Research SDK.

You can get sample codes with following steps.

[Sample research project](https://github.com/HealthcareResearchHub/sample-research)

Step 1 ...

Step 2 ...

## Customizing sample apps

Some modifications needed to perform our research.

### Change research introductions, consents and eligibility questions

To participate `MG Marker` research a person must agree with some conditions and meet the conditions.

Let's deliver information to them

For example, one of the features is an onboarding task that introduces a research study, checks eligibility, and requests data permission. 

Let’s see how we create an onboarding task for MG study. 

For the research introduction, the only thing we have to do is customize some value of intro model.

..coding instructions..

To check Eligibility, we are going to ask if they have ever experienced any special power. 

So let’s add a question for that. 

..coding instructions..

### Connect with back-ends

To integrate back-ends, a couple of codes should be added.

To get permissions of health data, we need to set target health data. 

In this demo, let’s collect heart rate, step count, and blood pressure. 

To upload health data into the backend, we can configure sync spec of each health data, respectively. 

..coding instructions..

## Let's build the app

Now, click run button on Android Studio.

If you have done correctly, you could see the app running like this.
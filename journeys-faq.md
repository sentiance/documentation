---
description: All FAQs below are subject to change. We update our applications frequently.
---

# Journeys FAQ

## Where can I find Journeys?

**Android**: Install Journeys directly from [Google Play](https://play.google.com/store/apps/details?id=com.sentiance.journeys&hl=en).

_Requirements operating system: Android 4.2 or higher phone sensors: Accelerometer, gyroscope, GPS data connections: Mobile data \(Edge/3G/4G\) and Wifi_

**iOS**: Install Journeys directly from the [App Store](https://apps.apple.com/be/app/journeys-by-sentiance/id984087229?l=nl).

_Requirements operating system: iOS 9.0 or higher iPhone: iPhone 4S or better data connections: Mobile data \(Edge/3G/4G\) and Wifi_

## What is a project code & where do I get one?

Project codes are dedicated identifiers for our client projects. If you are an individual user testing out our solutions you do not have to fill this in.

If you'd like to set up a dedicated environment please contact [sales@sentiance.com](mailto:sales@sentiance.com)

## I've installed with the wrong or without a project code while I should have used one.

Please contact your project point of contact or mailt to [support@sentiance.com](mailto:support@sentiance.com).

It is currently not possible to change this yourself due to privacy & GDPR concerns.

## App navigation & screen explanations

**Home screen: orientation** 

At the bottom of the app there are four options: Home, Profile, Timeline, Settings. Home: Your current status and location Profile: Your Lifestyle and Mobility Segments Timeline: All your Events and Moments arranged chronologically, day by day Settings: Details of your Journeys account, app and SDK version

**Home screen: events and moments** 

On the Home screen of the Journeys app you’ll see your current status and location — the Events and Moments, as we call them, that you’re currently experiencing. In the example, the user has been “Stationary” at their work location for the last two hours. They are “Working at work” in their semantic afternoon. This screen will be updated as we detect new Events and Moments throughout your day. For the full list of the Sentiance Events and Moments, please visit [https://developers.sentiance.com/docs](https://developers.sentiance.com/docs)

**Profile: segments**

The next screen to the right shows your Profile. The first view in the Profile screen shows your Segments. Segments are actionable properties/tags we learn about your behavior over time. They show what kind of lifestyle you have, if and how you go to work, in what geographical areas you live, what kind of drivers you are, etc.

These segments help our clients learn more about their customers and build better experiences. For the full list of the Sentiance Segments, please visit [https://developers.sentiance.com/docs/segments/](https://developers.sentiance.com/docs/segments/)

**Profile: stats**

The Stats view in the Profile screen provides detail about how you move. As you scroll, you’ll first see your Driving Scores \(a\), then your multi-modal Transport Distribution \(b\); and finally your Health Scores \(c\), which compare your activity, mobility and work/social balance vs. the rest of the Journeys population.

**Profile: locations** 

The Locations view in the Profile screen provides detail about the venues and places you’ve been, including your home and work location and all the other types of venues you’ve visited such as restaurants, shops, airports, cities etc.

**Timeline** 

The Timeline screen chronologically visualizes all of your Events and Moments that we detect throughout each day. In the example here, the user was at home in Brooklyn, NY on Saturday, November 17th from midnight to 12:35 \(a\). By scrolling down the timeline, you see at 12:35pm the user went for a walk near a park \(b\). Click on the map in the timeline to get more detail of this walking Event \(c\). Providing feedback to Sentiance is easy. To confirm \(or change\) this walking Event, first select Feedback in the top right. \(See timeline: feedback\)

**Timeline: feedback** 

In the Feedback view, you’ll see the other transport mode options, such as Car, Running, Biking, Train, etc. You’ll notice the original detection is outlined in blue. Select the option that matches the actual mode of transportation. We’ve selected Walking in this example, and it changes to green. Similarly, you can provide feedback on our Moments. Here the user is presented with the Moments “Nearby home” and “Nearby work.” Let’s say that only the “Nearby home” Moment is correct. Simply select the check mark for “Nearby home” to accept it, and the x mark for “Nearby work” to reject it. The view is then updated. In the Detections view, you will see the meta data on our Events and Moments.

**Timeline: detections** 

In this example you’ll see the changes we made to the Moments are reflected and only “Nearby home” is shown. The Event was confirmed to be walking. In addition, the Start and End time of the trip are shown in the user’s local time zone, as well as the metric distance of the trip.

**Settings** 

In the Settings view you will find detail about your Journeys account, including your unique User ID, the app and SDK version and a variety of other settings.

## I do not see any detections

**I have installed the app less than 3 days ago**

Our platform needs a certain amount of data before we can start identifying your events, moments & segments correctly. Please make sure you've been tracking with the permissions set correctly for at least a few days. 

**I have installed the app more than 3 days**

* Make sure your device has the required specifications.
* Make sure you've given the right permissions. 
* Specific android devices may require whitelisting.
  * Contact your project point of contact or [support@sentiance.com](mailto:support@sentiance.com) if you require assistance with this.

## Journeys detects my home as my work

It can take up to 2-3 weeks for Journeys to accurately detect your routines and home/work locations. If you went on holiday or business trip in that period, it might take a bit longer.

## I moved to a new home \(or: I changed jobs recently\) and now my detections are all wrong

I can take up to three weeks after a move before Journeys picks up on it. Stay tuned!

## I have installed Journeys on multiple devices, will this cause problems?

Journeys is currently not built to handle this kind of behaviour. However our SDK has the possibility to handle this use case when implemented in your application.

## I gave feedback on an incorrect event, but Journeys made the same mistake again

Feedback is used to train our models and improve our algorithms at Sentiance, but is not used for real-time and online learning for now. Feedback is appreciated but will not solve mistakes immediately

## The timeline looks different today compared to before

We have a great blog post around this topic that you can read [here](https://www.sentiance.com/2019/07/03/when-context-is-king-time-is-queen/). But yes detections may change after the fact. Your current actions may give us more clues and insights into your past behaviour and thus we may want to retroactively update the detections to be more accurate. 

## I see different scores in journeys but do not know what they mean

These scores aim to demonstrate our best effort to provide you with a number that you could use to compare drivers and take actions upon. Please note that these may change often.

## How can I make Journeys stop tracking me temporarily if I visit certain places?

We don't have built-in functionality for that at this time. You could disable location tracking on the OS level to make this happen.

## The detected segments \(or other data points\) are incorrect, how can I change them?

_At the moment it's not possible to change detections on the fly._

It's important to note that Journeys is for demo purposes only, it is what we detect for you out of the box. With an actual integration we can tweak certain parameters to achieve different results.   





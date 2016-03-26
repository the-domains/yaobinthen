---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: Android ProgressBar not showing when animations are turned off
datePublished: '2016-03-26T00:54:19.630Z'
dateModified: '2016-03-26T00:51:31.161Z'
title: Android ProgressBar not showing
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-03-26-android-progressbar-not-showing.md
published: true
url: android-progressbar-not-showing/index.html
_type: Article

---
So lately I spent some significant amount of time pondering why my Android ProgressBar is not showing up although the code works correctly. If you have the same problem, take a look in the Developer options in Settings, and make sure the following 3 settings are not turned off.

* Window animation scale
* Transition animation scale
* Animator duration scale

These settings will disable any animations in Android, so if you're wondering why your animations aren't working, make sure it's not caused by these settings.

I had these settings turned off on my phone while working on Espresso testing in Android. It is recommended to have these settings turned off to avoid test flakiness.

Next up, I will be posting on Espresso testing and Appium testing, so stay tuned!
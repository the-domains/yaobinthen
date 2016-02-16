---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: implementing polling in relayjs
datePublished: '2016-02-16T09:14:28.182Z'
dateModified: '2016-02-16T09:14:09.509Z'
title: polling in relay
author: []
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
sourcePath: _posts/2016-02-16-polling-in-relay.md
published: true
url: polling-in-relay/index.html
_type: Article

---
Recently I have been working on a chat related app using Relay + React Native, and came across a problem that has been a show blocker for a week.

Relay has been designed for infinite scrolling rather than pagination. Due to this nature, getting previous chats were easy, but not for getting newest messages. When you get current available messages, Relay assumes there's no more newer messages. An obvious example is Facebook, you can scroll indefinitely down, but you tends to refresh the page to get the back to the top for newer feeds.

However it is not ideal to trigger a _forceFetch_ to get all the data again especially on a mobile device.

After a week of struggle, the answer was actually quite obvious, which is to use another field, _newMessages_ which returns a list of new messages given a timestamp, together with the original _messagesConnection_ which returns the messages during first load and messages in the past. By having Relay to return two array of data, I have to maintain a copy of the combined data to be displayed.

Now, to poll for new messages, I simply supply the timestamp to _newMessages _at an interval, using Relay's _setVariables._

See this [stackoverflow post][0] for more technical detail.

[0]: http://stackoverflow.com/questions/35129716/how-to-fetch-for-new-edge-using-polling-method
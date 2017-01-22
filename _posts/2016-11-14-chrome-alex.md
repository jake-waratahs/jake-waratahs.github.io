---
title: Introducing chrome-alex!
subtitle: Check for inconsiderate language in your browser
layout: post
---

At 6 am on Monday July 25th, 2016, I woke up on the ground, in a tent in Yelgun, NSW, about thirty minutes drive north of Byron Bay. I got dressed, brushed my teeth and trudged two kilometres to the bus station, where I caught a shuttle to Coolangatta airport, and then a flight down to Sydney.

The three days prior had been the Splendour in the Grass music festival, which was incredible, but that's another story.

From Sydney airport, I got a cab to Uni, where there was a meeting among student societies going on to discuss how to promote diversity in Computing. I was unshaven, hadn't showered for days, and was exhausted. After the meeting I went home, had a shower, went back to Uni to go to a lecture, then went back home, packed my bags, and went back to the airport to get a flight to San Francisco.

That's not an abnormal travel schedule in my family, but this post isn't about that - that post is about what happened and what came out of that meeting.

<!--break-->

The meeting was called by our head of school and development office. At the meeting was [Aubrey Blanche](https://twitter.com/adblanche), Atlassian's Global Head of Diversity and Inclusion, as well as some other absolute legends including my friends DP, Bec, Adam and the other Adam. We had a really good chat about the issues facing all of us in the industry, and some things we could be doing.

During the meeting, Aubrey mentioned that there was a JavaScript library called "alex", which scanned files for insensitive or offensive language. She said that she wished HipChat (Atlassian's corporate messaging application) had some capacity to do this in messages, and told me I should write a plugin to implement that.

Well I'm sorry Aubrey, I've let you down. I've gone and built a Google Chrome extension instead.

## What is it?
chrome-alex is an extension for the Chrome browser that I wrote. I started writing it way back in August and then life and semester got in the way, so I only got to put the finishing touches on it last week. It has since been published in the Chrome web store. You can download it [here](https://chrome.google.com/webstore/detail/chrome-alex/ljbneoldiojfddioppeaaklbfaocmdkg).

If you click on the "A" in the top corner of your screen, a list will pop up with the language on the page that you may want to reconsider using.

<img src="/img/alex1.png" class="ui centered medium image" />

## How does it work?
So Chrome extensions have three possible components: Background Pages, Content Scripts and Popups. Without getting too technical, Background pages are exactly what they sound like (pages running in the background), content scripts are injected into the current page you're viewing, and popups are what you see when you open up an extension.

So when you click the icon, it sends a message to the background page to get the text on the web page you're viewing. Once it has this, it runs the alex JavaScript library over it, and then sends a message back to the popup saying "hey, here's all the bad words on the page". The popup then displays them all in a list back to you, the user.

<img src="/img/alex2.png" class="ui centered medium image" />

## Limitations
Unfortunately, there are a few limitations of the extension that I haven't been able to work around just yet, but I'll keep trying:

-  It probably won't work on your Facebook feed or other very complex web pages. This is because the DOM is so deeply nested, it takes a long time to retrieve the text on the page for processing.
- It doesn't work on Gmail. This is one I need to investigate more because I think checking your language while composing an email is a basic use case for this.

## When should I use it?
If you're ever writing, reading or reviewing something online, you can use this to spot any language that you might consider changing. Fingers crossed we can all use this to be a bit more empathetic online 👌

## How can I get it?
[This is the download link](https://chrome.google.com/webstore/detail/chrome-alex/ljbneoldiojfddioppeaaklbfaocmdkg)

[This is the source code, if you're interested](https://github.com/jake-waratahs/chrome-alex)
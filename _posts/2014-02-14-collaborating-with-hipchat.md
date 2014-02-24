---
layout: post
title: "Collaborating With HipChat"
description: "Group Chat & IM Built for Teams"
category: 
tags: []
---
{% include JB/setup %}

<blockquote>
	<p>Group Chat &amp; IM Built for Teams</p>
</blockquote>

[HipChat](https://www.hipchat.com) supports group chat and one-on-one private messaging via web, desktop and mobile. HipChat is free for teams of five or less and priced at [$2/user/month](https://www.hipchat.com/pricing) for larger teams. When you signup, your HipChat instance will be setup on a hipchat.com subdomain (there's also a local install version in [beta](https://www.hipchat.com/server)). Once you're setup, it's time to really make HipChat shine with its API and and Add-ons!

<img src="/assets/images/posts/hipchat_integrations.png" class="pull-right post-image" />
API
-----
First, checkout HipChat's [Getting Started](https://www.hipchat.com/docs/api) guide. Once you've generated an auth token, you can setup a variety of [3rd party integrations](https://www.hipchat.com/integrations) or [build your own](https://www.hipchat.com/docs/api/libraries). For example, at [Tailwind](http://tailwindapp.com), we've added integration for our project management tool [Pivotal Tracker](http://danielsposito.com/blog/2014/01/24/collaborating-with-pivotal-tracker). This allows us to receive useful notifications within HipChat anytime a team member adds or edits a Pivotal Tracker Story.

Additionally, [HipChat CLI](http://github.com/hipchat/hipchat-cli) made it really easy to send relevant notifications to our Engineering group chat room. For example, commit descriptions and changeset links (via GitHub) are sent as notifications when new code changes are pushed to one of our repos. We receive similar notifications during deployments as well.

<img src="/assets/images/posts/hipchat_emoticons.png" class="pull-right post-image" />
Add-ons &amp; Emoticons
----------------------
HipChat supports several [Add-ons](https://marketplace.atlassian.com/plugins/app/hipchat/popular) such as Quote of the Day (highly recommended) and BitBucket Connector. It also includes a [ton](http://hipchat-emoticons.heroku.com) of fun emoticons and you can upload any image to create your own. There's nothing more fun than having custom emoticons that represent your team's lingo and inside jokes!

What Do You Think?
------------------
Does your team use HipChat? What other chat services have you used? Let me know what has or hasn't worked for you [@smwrxforever](https://twitter.com/smwrxforever).

<br />
<p class="text-muted">
	<em>I originally wrote this post for the <a href="http://tailwindapp.wpengine.com/collaborating-with-hipchat">Tailwind Engineering blog</a>. I'm cross-posting it here.</em>
</p>

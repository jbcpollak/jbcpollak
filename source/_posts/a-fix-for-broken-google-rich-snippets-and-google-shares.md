title: A Fix for Broken Google Rich Snippets and Google+ Shares
tags:
  - Content-Encoding
  - google
  - Google Plus
  - Hacked
  - HTML
  - PHP
  - Rich Snippets
  - Validator
  - wordpress
id: 385
categories:
  - Tech
date: 2011-09-15 01:41:24
---

Recently I have been struggling with an issue where links to my website do not generate previews in Google+. Instead, the user gets the error _"Could not load website. - Retry"_. When they try and retry, the error does not go away. Needless to say, although my readership is pretty low, that isn't helping much.

When I started poking around, I found that Google+ uses Google's "Rich Snippet" system. Google has released a [Rich Snippet Testing Tool](http://www.google.com/webmasters/tools/richsnippets "Google"). The tool is great, and it helps you tweak your HTML so you get the correct snippet content.

...Except in my case, where the tool just reported _"Could not fetch web page."_. Not helpful. Why a better error descriptor isn't given, I don't know.

This article will explain how I got to the bottom of the problem (despite Google's useless error messages) and how you can look for similar issues.

<!--more-->

When I realized I was getting intentionally vague responses from the Google tools, I [posted](http://www.google.com/support/forum/p/Webmasters/thread?tid=1a2266a505794a99&hl=en&fid=1a2266a505794a990004ace8be1dfd09) to Google's Webmaster Central forums, but didn't get a useful answer.

After a few days of thinking about it, I got the idea to try my website on the [W3 HTML validator site](http://validator.w3.org/ "HTML Validator").

The validator gave me a new error. I lost the actual text, but it said it could not understand _Content-Encoding 'none'_. Finally, we're getting somewhere.

I started doing research into why Wordpress might be sending the wrong Content-Encoding, but didn't find anything. So I logged onto my website, and grepped for 'Content-Encoding'. Nothing really exciting jumped out at me.

_But_, while I was logged in, I noticed some suspicious PHP files. And then I noticed at the top of wp-config.php a line of PHP that started like this: `eval(base64_decode("aWYoZnV`.

Oh... that's a sure sign I've been hacked. So I followed the instructions [here](http://blog.sucuri.net/2010/05/new-attack-today-against-wordpress.html), and removed the hacked code and suspicious PHP files.

Then I went to the validator, and sure enough, the Content-Encoding had changed, so it was able to actually run the validator. So I tried the Rich Snippet Testing Tool, and sure enough, now it works too! Which means Google+ shares work again!

So, the bottom line is, if you are having trouble with sharing your website on Google+, check your Content-Encoding, and make sure you haven't been hacked.

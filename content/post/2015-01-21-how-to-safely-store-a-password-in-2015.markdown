---
categories:
- security
- passwords
comments: true
date: 2015-01-21T20:01:31Z
title: How To Safely Store A Password In 2015
url: /2015/01/21/how-to-safely-store-a-password-in-2015/
---

I stumbled onto Coda Hale's post about how to [safely store a password](http://codahale.com/how-to-safely-store-a-password/) earlier this week. In it, he discusses how to safely store a users' password on your system in order to authenticate that user.

Basically, he advocates using bcrypt. However, that post was written five years ago ( actually, five years ago this month ).

How about something (possibly) better?

<!--more-->

# Use A Single Sign-On (SSO) Provider

Use [SSO](https://lastpass.com/enterprise/cloud-sso). Use [SSO](https://www.atlassian.com/software/crowd/overview). Use [SSO](https://www.pingidentity.com/en/products/pingone.html). Use [SSO](https://www.onelogin.com/product/sso). Use [SSO](http://www.forgerock.com/en-us/platform/identity-management/). Use [SSO](https://www.apereo.org/cas). Use [SSO](http://rubycas.github.io/). Use [SSO](https://developer.github.com/v3/oauth/). Use [SSO](https://developers.facebook.com/docs/facebook-login/v2.2). Use [SSO](https://dev.twitter.com/web/sign-in). Use [SSO](https://dev.twitter.com/twitter-kit/android/twitter-login). Use [SSO](https://developers.google.com/+/).

# Why The Hell Should I?

First, creating *yet another user account* is not something most users want to do. Passwords are insecure enough without having to try and remember which password goes with which site. While there are extensions such as [LastPass](https://lastpass.com/), they don't come with the browser. Without something built into the browser that can automatically generate strong passwords and sync them between devices, I think it's a safe bet that when asked to create yet another password users will probably just end up using the same super-insecure password they're using on every other site.

Second, what about two factor authentication? Do you want to be the one in charge of implementing a two-factor scheme? Are you sure that you'll get it correct, and never ever break it? Are you going to use up users text message allocations by sending them a code ( thanks for that, Twitter ), or are you going to use Google Authenticator? What if your users want to use a security key like the [Yubikey NEO](https://www.yubico.com/products/yubikey-hardware/yubikey-neo/)?

Do you really want to be working on implementing user authentication, when you could be working on something awesome instead?

# SSO Solves This

Let your users sign in with Google. Or Facebook. Or Twitter. Or GitHub. Or whatever SSO you want. You can even buy SSO solutions to host inside your network if you need something that will never see the web outside your corporate firewall.

What I'm trying to get at is this: why worry about passwords at all? Sure, you can use bcrypt and store the password yourself. But now you've introduced yet another password into the world. Even with bcrypt's strengths, the world doesn't need more passwords. I really don't think it does. I think it needs less.

Every site that requires a password to log in is another site that can be used as a vector for [phishing](http://en.wikipedia.org/wiki/Phishing). If a user never creates a password for your site, then they can't accidentally give it out -- because you don't have a login screen to be faked.

Plus, letting a user sign in with some other account means that they don't have to spend time creating an account. Most sites get account creation wrong anyways; all you should need is an email and password ( *maaaaybe* a username, depending on what your site does ).

# tl;dr

Don't use bcrypt. Use an SSO provider.

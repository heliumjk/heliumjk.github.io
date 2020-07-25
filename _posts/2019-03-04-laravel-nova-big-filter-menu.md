---
id: 79
title: 'Laravel Nova &#8211; Big Filter Menu'
date: 2019-03-04T22:45:54-08:00
author: ed@normalllc.com
layout: post
guid: https://edanisko.com/?p=79
permalink: /laravel-nova-big-filter-menu/
categories:
  - Laravel
  - Nova
  - Packages
---
Laravel Nova is a great way to get an admin panel up and running. If you built your project with Laravel, Nova will fit right on top. You can create resources based on your models. The resources have all sorts of fields so you can display<!--more--> and edit your data. You can create metrics for fancy displays of certain values. It all ties nicely together with custom filters firing off axios queries into the nova api so you can zip through your data as light speed.

It&#8217;s really great. All except the filter menu. It&#8217;s a tiny button that looks like a filter jammed on the right side of the screen. It&#8217;s so small I can hardly stand it. As you might expect, having been built by the creators of Laravel, Nova is hyper extendible. So I hacked it out and made a nice looking filter menu that stays open. It very easy to install and use.

Without further ado, introducing [Nova-Big-Filter](https://packagist.org/packages/nrml-co/nova-big-filter).
---
layout: post
title: "Upgrading to Django 1.5"
date: 2013-03-04
comments: true
link: true
categories:
- Software
- Python
- Django
tags:
- Python
- Django
---

Recently I upgraded a Django site from 1.4.5 to the new [1.5](https://docs.djangoproject.com/en/dev/releases/1.5/) release. I decided to upgrade before my Django app got more complex and I wanted to check out the new [configurable user model](https://docs.djangoproject.com/en/dev/topics/auth/customizing/#auth-custom-user). I'll cover some problems I had when upgrading and show replacements for some deprecated methods.

I did a quick ```pip install django==1.5``` and hoped for the best. Unfortunately my heart sank when I ran ```python manage.py runserver``` after upgrading and was greeted with an error message (DEBUG set to true in settings) about some import statements. Nothing in software comes easy.

Like a lot of sites on the web, my Django app has a [robots.txt](http://www.robotstxt.org/) and a [humans.txt](http://humanstxt.org) file. With Django 1.4.5 I had been serving these text files with the ```direct_to_template``` method, with a mimetype of "text/plain." I realized I'd have to switch to Django's shiny new class-based generic views and remove the deprecated method. Note that "mimetype" has been changed to "content_type" also.

``` python urls.py
from django.conf.urls import patterns, url
from django.views.generic import TemplateView

urlpatterns = patterns('',
    url(r'^robots\.txt$', TemplateView.as_view(template_name='robots.txt', content_type='text/plain')),
    url(r'^humans\.txt$', TemplateView.as_view(template_name='humans.txt', content_type='text/plain')),
)
```

Another problem I had was the invalid import of ```from django.views.generic.simple import redirect_to``` which has been deprecated in 1.5. To get around that I changed my view code to use ```redirect``` instead.

``` python views.py
from django.shortcuts import redirect

def page_view(request):
    # View code here
    return redirect('/other-page/')
```

You could also use Django's class-based generic views to put the redirect in a URL rule in your urls.py file.

``` python urls.py
from django.conf.urls import patterns, url
from django.views.generic import RedirectView

urlpatterns = patterns('',
    url(r'^page-url', RedirectView.as_view(url='/other-page/'))
)
```

I hope these examples help someone out who had the same problems as me. I was still impressed with how seamless the upgrade to 1.5 was and I had fewer things to fix than I thought I would. Upgrade early and upgrade often!

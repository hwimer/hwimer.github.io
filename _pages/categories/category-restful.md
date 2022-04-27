---
title: "Restful"
layout: archive
permalink: categories/restful
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories.restful%} 
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}

---
title: "Modern Software"
layout: archive
permalink: categories/modernSoftware
author_profile: true
sidebar_main: true
---


{% assign posts = site.categories.modernSoftware%} 
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
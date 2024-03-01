---
layout: page
permalink: /talks/
title: 
description: #I am open to talk opportunities if you are interested in my works.
nav: false
nav_order: 3
---

<!-- pages/talks.md -->
<div class="talks">
    <div class="header-bar">
        <h1>Talks</h1>
        <p>I really like to talk about science, music, and anything I'm passionate about. I often tell jokes during talks, sometimes people laugh. <a href="mailto:ytaoudi@student.ethz.ch">Invite me!</a>.</p> 
    </div>
{% if site.talks != blank -%} 
<div class="table-responsive">
    <table class="table table-sm table-borderless">
    {%- assign talks = site.talks | reverse -%} 
    {% for item in talks %} 
    <tr>
        <th scope="row">{{ item.date | date: "%b %-d, %Y" }}</th>
        <td>
        {% if item.inline -%} 
            {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
        {%- else -%} 
            <a class="talks-title-with-redirect" href="{{item.redirect_link}}">{{ item.title }}</a>
            <p> {{item.description}}</p>
        {%- endif %} 
        </td>
        <td>
            <span class="event">{{ item.event }}</span>
            <span class="talks-place">{{ item.location }}</span>
        </td>
    </tr>
    {%- endfor %}
    </table>
</div>
{%- else -%} 
<p>No talks so far...</p>
{%- endif %} 
</div>
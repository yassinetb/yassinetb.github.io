---
layout: default
permalink: /blog/
title: Blog
nav: false
pagination:
  enabled: true
  collection: posts
  permalink: /page/:num/
  per_page: 8
  sort_field: date
  sort_reverse: true
  trail:
    before: 1 # The number of links before the current page
    after: 3 # The number of links after the current page
---

<div class="talks">
    <div class="header-bar">
        <h1>Blog</h1>
        <p>I write down random thoughts from time to time. Maybe you enjoy some of them? 
    </div>
</div>

<br />

<div class="post">
  <ul class="post-list">
    {% assign sorted_posts = site.posts | sort: 'date' | reverse %}
    {% for post in sorted_posts %}
      {% if post.show == true %}
        <li>
          <div class="blog-display">
            <div class="blog-display">
              <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
              <p>{{ post.date | date: '%B %d, %Y' }}</p>
              <p>{{ post.content | strip_html | truncatewords: 50 }}</p>
            </div>
          </div>
        </li>
      {% endif %}
    {% endfor %}
  </ul>

</div>
 


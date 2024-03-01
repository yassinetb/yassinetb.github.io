---
layout: default
title: Past Projects
permalink: /past_projects/
description: Currently looking for students to collaborate on these projects - please reach out! 
nav: false
horizontal: false
related_posts: false
pagination: true
---

<div class="projects">
  <div class="header-bar">
    <h1>Past Projects</h1>
    <p>Some previous projects I've worked on.</p> 
  </div>
  <!-- Sort projects by end date -->
  {% assign sorted_projects = site.past_projects | sort: "end_date" | reverse %}
  <!-- Loop through sorted projects -->
  {% for project in sorted_projects %}
  <div class="project">
    <br />
    <h2>{{ project.title }}</h2>
    <p class="project-info">{{ project.description }}</p>
    <!-- Links to code and paper -->
    <div class="collaborators">
      <p class="project-info"><strong>Workforce:</strong>
        {% for collaborator in project.collaborators %}
          {{ collaborator }}
          {% unless forloop.last %}, {% endunless %}
        {% endfor %}
      </p>
      {% if project.institution %}
      <p class="project-info" ><strong>Institution:</strong> {{ project.institution }}</p>
      {% endif %}
      <div class="dates">
        {% if project.start_date and project.end_date %}
        <p class="project-info"><strong>Date:</strong> {{ project.start_date | date: "%b %Y" }} - {{ project.end_date | date: "%b %Y" }}</p>
        {% elsif project.start_date %}
        <p class="project-info"><strong>Start Date:</strong> {{ project.start_date | date: "%b %Y" }}</p>
        {% elsif project.end_date %}
        <p class="project-info"><strong>End Date:</strong> {{ project.end_date | date: "%b %Y" }}</p>
        {% endif %}
      </div>
       <div class="links">
        {% for link in project.links %}
            <a href="{{ link.url }}" target="_blank"><u>{{ link.name }}</u></a>{% unless forloop.last %}&nbsp;&nbsp;{% endunless %}
        {% endfor %}
        </div>
    </div>
    <!-- Collaborators and Institution -->
  </div>
  <hr> <!-- Separator -->
  {% endfor %}
</div>



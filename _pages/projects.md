---
layout: default
title: Open Projects
permalink: /projects/
description: Currently looking for students to collaborate on these projects - please reach out! 
nav: false
horizontal: false
related_posts: false
pagination: true
---

<div class="projects">
  <div class="header-bar">
    <h1>Open Projects</h1>
    <p>These projects are currently offered for prospective students. If anything interests you, 
  please <a href="mailto:{{%site.email%}}">email me directly</a> to inquire and talk! If you'd like to know
  what it's like to work with me and what kind of students I'm looking for, please have a read <a href="/work-with-me">here</a>.</p> 
  </div>
  {% if site.enable_project_categories and page.display_categories %}
    <!-- Display categorized projects -->
    {% for category in page.display_categories %}
      <a id="{{ category }}" href=".#{{ category }}">
        <h2 class="category">{{ category }}</h2>
      </a>
      {% assign categorized_projects = site.projects | where: "category", category %}
      {% assign sorted_projects = categorized_projects | sort: "importance" %}
      <!-- Generate cards for each project -->
      {% if page.horizontal %}
        <div class="container">
          <div class="row row-cols-2">
            {% for project in sorted_projects %}
            {% if project.show == true %}
                {% include projects_horizontal.liquid %}
            {% endif %}
            {% endfor %}
          </div>
        </div>
      {% else %}
        <div class="grid">
          {% for project in sorted_projects %}
            {% if project.show == true %}
            {% include projects.liquid %}
            <hr> <!-- Separator -->
            {% endif %}
          {% endfor %}
        </div>
      {% endif %}
    {% endfor %}
  {% else %}
    <!-- Display projects without categories -->
    {% assign sorted_projects = site.projects | sort: "importance" %}
    <!-- Generate cards for each project -->
    {% if page.horizontal %}
      <div class="container">
        <div class="row row-cols-2">
          {% for project in sorted_projects %}
            {% if project.show == true %}
            {% include projects_horizontal.liquid %}
            {% endif %}
          {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="grid">
        {% for project in sorted_projects %}
          {% if project.show == true %}
          <div class="project">
            <a href="{{ project.url }}">
              <h2 class="project-title">{{ project.title }}</h2>
            </a>
            {% if project.authors %}
            <p class="project-info"><strong>Supervisors:</strong> 
                {% for supervisor in project.authors %}
                {{ supervisor.name }}
                {% unless forloop.last %}, {% endunless %}
                {% endfor %}
            </p>
            {% endif %}
            {% if project.type %}
            <p class="project-info"><strong>Project Type:</strong> {{ project.type | join: ', ' }}</p>
            {% endif %}
            {% if project.duration %}
            <p class="project-info"><strong>Project Duration:</strong> {{project.duration}}</p>
            {% endif %}
          </div>
          <hr> <!-- Separator -->
          {% endif %}
        {% endfor %}
      </div>
    {% endif %}
  {% endif %}
</div>
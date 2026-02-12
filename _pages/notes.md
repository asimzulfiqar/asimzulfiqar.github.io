---
layout: default
permalink: /notes/
title: Notes
description: Short thoughts, reflections, and mini blogs on IoT development, freelancing, and software engineering.
nav: true
nav_order: 3
---

<div class="post">
  <div class="header-bar">
    <h1>{{ page.title }}</h1>
    <h2>{{ page.description }}</h2>
  </div>

  <div class="notes-feed">
    {% assign notes = site.notes | reverse %}
    {% for note in notes %}
      <article class="note-entry">
        <div class="note-meta">
          <time datetime="{{ note.date | date_to_xmlschema }}">
            {{ note.date | date: '%B %d, %Y' }}
          </time>
          {% if note.tags %}
            <span class="note-tags">
              {% for tag in note.tags %}
                <span class="tag">{{ tag }}</span>
              {% endfor %}
            </span>
          {% endif %}
        </div>

        {% if note.inline %}
          <div class="note-content">
            {{ note.content }}
          </div>
        {% else %}
          <h2 class="note-title">
            <a href="{{ note.url | relative_url }}">{{ note.title }}</a>
          </h2>
          <div class="note-content">
            {{ note.content }}
          </div>
        {% endif %}
      </article>

      {% unless forloop.last %}
        <hr class="note-separator">
      {% endunless %}
    {% endfor %}

    {% if site.notes.size == 0 %}
      <p class="text-muted">No notes yet...</p>
    {% endif %}
  </div>
</div>

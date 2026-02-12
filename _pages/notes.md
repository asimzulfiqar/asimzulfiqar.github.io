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

<style>
  .notes-feed {
    max-width: 720px;
    margin: 2rem auto;
  }

  .note-entry {
    margin-bottom: 3rem;
  }

  .note-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
    color: var(--global-text-color-light);
    font-size: 0.9rem;
  }

  .note-tags {
    display: flex;
    gap: 0.5rem;
  }

  .note-tags .tag {
    background: var(--global-bg-color);
    border: 1px solid var(--global-divider-color);
    padding: 0.2rem 0.6rem;
    border-radius: 4px;
    font-size: 0.85rem;
  }

  .note-title {
    margin: 0.5rem 0 1rem 0;
    font-size: 1.5rem;
    font-weight: 600;
    line-height: 1.3;
  }

  .note-title a {
    color: var(--global-text-color);
    text-decoration: none;
  }

  .note-title a:hover {
    color: var(--global-theme-color);
  }

  .note-content {
    font-size: 1rem;
    line-height: 1.8;
    color: var(--global-text-color);
  }

  .note-content p {
    margin-bottom: 1.5rem;
  }

  .note-content h2,
  .note-content h3,
  .note-content h4 {
    margin-top: 2rem;
    margin-bottom: 1rem;
  }

  .note-content ul,
  .note-content ol {
    margin-bottom: 1.5rem;
    padding-left: 2rem;
  }

  .note-content li {
    margin-bottom: 0.5rem;
  }

  .note-content blockquote {
    border-left: 3px solid var(--global-theme-color);
    padding-left: 1.5rem;
    margin: 1.5rem 0;
    color: var(--global-text-color-light);
    font-style: italic;
  }

  .note-content code {
    background: var(--global-code-bg-color);
    padding: 0.2rem 0.4rem;
    border-radius: 3px;
    font-size: 0.9em;
  }

  .note-content pre {
    background: var(--global-code-bg-color);
    padding: 1rem;
    border-radius: 6px;
    overflow-x: auto;
    margin: 1.5rem 0;
  }

  .note-content pre code {
    background: transparent;
    padding: 0;
  }

  .note-separator {
    border: none;
    border-top: 1px solid var(--global-divider-color);
    margin: 3rem 0;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .notes-feed {
      max-width: 100%;
      padding: 0 1rem;
    }

    .note-title {
      font-size: 1.3rem;
    }

    .note-meta {
      flex-direction: column;
      align-items: flex-start;
      gap: 0.5rem;
    }
  }
</style>

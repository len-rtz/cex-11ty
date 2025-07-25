---
title: "Latest News"
layout: base.njk
---

<h1>Latest News</h1>

<section class="grid">
{% set newsLimit = 3 %}
{% for post in collections.news %}
  {% if loop.index <= newsLimit %}
  <article>
    <header>
      <h3><a href="{{ post.url }}">{{ post.data.title }}</a></h3>
      <p><small>{{ post.date | date("MMM dd, yyyy") }}</small></p>
    </header>
    <p>
      {% if post.data.excerpt %}
        {{ post.data.excerpt }}
      {% else %}
        {{ post.templateContent | striptags | truncate(150, true, "…") }}
      {% endif %}
    </p>
    <footer>
      <a href="{{ post.url }}" role="button" class="secondary">Read more</a>
    </footer>
  </article>
  {% endif %}
{% else %}
  <p>No news posts available.</p>
  <p>Debug: collections.news length = {{ collections.news.length }}</p>
{% endfor %}
</section>

<p><a href="/apply/" role="button">Join our community today!</a></p>
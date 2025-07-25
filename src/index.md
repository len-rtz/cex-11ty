---
title: Welcome!
layout: base.njk
---
# Welcome

Founded in {{ sportsclub.founded }}, we are located in {{ sportsclub.location }} and dedicated to our mission: *{{ sportsclub.mission }}*

## What We Offer

- **Professional Coaching** - Train with certified coaches who bring years of experience
- **Multiple Teams** - From youth development to competitive adult leagues
- **Modern Facilities** - Well-maintained fields and training equipment
- **Active Community** - Connect with fellow sports enthusiasts!

## Latest News

<section class="news-preview">
{% for post in collections.news | slice(0, 2) %}
  <article class="news-card">
    <div class="news-content">
      <h3><a href="{{ post.url }}">{{ post.data.title }}</a></h3>
      <p class="news-date">{{ post.date | date("MMM dd, yyyy") }}</p>
      <p class="news-excerpt">
        {% if post.data.excerpt %}
          {{ post.data.excerpt }}
        {% else %}
          {{ post.templateContent | striptags | truncate(120, true, "…") }}
        {% endif %}
      </p>
      <a href="{{ post.url }}" class="read-more">Read more →</a>
    </div>
  </article>
{% endfor %}
</section>

<div class="text-center">
  <a href="/news/" class="secondary-button">View All News</a>
</div>


## Get Involved

Ready to join our athletic community? We welcome players of all skill levels!

- **Email:** {{ sportsclub.email }}
- **Phone:** {{ sportsclub.phone }}
- **Address:** {{ sportsclub.address }}

[Apply to Join →](/apply/)
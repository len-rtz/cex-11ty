---
title: About Us
layout: base.njk
---

# About the Sports Club# Welcome to {{ sportsclub.name }}

Founded in {{ sportsclub.founded }}, we are located in {{ sportsclub.location }} and dedicated to our mission: *{{ sportsclub.mission }}*

## Our Teams

We currently have {{ teams.length }} active teams across different sports and divisions:

{% for team in teams %}
### [{{ team.name }}](/teams/{{ team.id }}/)
**Sport:** {{ team.sport }} | **Division:** {{ team.division }} | **Founded:** {{ team.founded }}

{{ team.description }}

{% set coach = members | findById(team.coach) %}
**Coach:** {% if coach %}{{ coach.name }}{% else %}TBA{% endif %}

**Members:** {{ team.members.length }} active players

---
{% endfor %}

## Training Schedule

We offer {{ training.length }} regular training sessions throughout the week:

{% for session in training %}
{% set team = teams | findById(session.team) %}
- **{{ session.title }}** - {{ session.day }} at {{ session.time }} ({{ session.duration }} min)
  - Team: {% if team %}[{{ team.name }}](/teams/{{ team.id }}/){% else %}{{ session.team }}{% endif %}
  - Location: {{ session.location }}
{% endfor %}

[View Full Training Schedule →](/training/)

## Get Involved

Ready to join our athletic community? We welcome players of all skill levels!

- **Email:** {{ sportsclub.email }}
- **Phone:** {{ sportsclub.phone }}
- **Address:** {{ sportsclub.address }}

[Apply to Join →](/apply/)
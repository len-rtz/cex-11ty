---
title: Our Teams
layout: base.njk
---

# Our Teams

{{ sportsclub.name }} is home to {{ teams.length }} competitive teams across multiple sports and divisions.

{% for team in teams %}
## [{{ team.name }}](/teams/{{ team.id }}/)

**Sport:** {{ team.sport }} | **Division:** {{ team.division }} | **Founded:** {{ team.founded }}

{{ team.description }}

{% set coach = members | findById(team.coach) %}
**Coach:** {% if coach %}{{ coach.name }}{% if coach.coaching_license %} ({{ coach.coaching_license }}){% endif %}{% else %}TBA{% endif %}

### Training Schedule
{% for training_id in team.training_sessions %}
  {% set session = training | findById(training_id) %}
  {% if session %}
- **{{ session.title }}:** {{ session.day }} at {{ session.time }} - {{ session.location }}
  {% endif %}
{% endfor %}

[View Full Team Details →](/teams/{{ team.id }}/)

---
{% endfor %}

## Join a Team

Interested in joining one of our teams? [Contact us](/apply/) to learn more about tryouts and registration.
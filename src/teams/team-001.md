---
title: "Team Details"
layout: base.njk
permalink: "/teams/team-001/"
teamId: "team-001"
---

{% set team = teams | findById(teamId) %}

# {{ team.name }}

**Sport:** {{ team.sport }} | **Division:** {{ team.division }} | **Founded:** {{ team.founded }}

{{ team.description }}

## Team Information

{% set coach = members | findById(team.coach) %}
**Coach:** {% if coach %}{{ coach.name }}{% if coach.coaching_license %} ({{ coach.coaching_license }}){% endif %}{% else %}TBA{% endif %}

**Team Size:** {{ team.members.length }} members

### Training Schedule
{% for training_id in team.training_sessions %}
{% set session = training | findById(training_id) %}
{% if session %}
- **{{ session.title }}:** {{ session.day }} at {{ session.time }} - {{ session.location }}
{% endif %}
{% endfor %}

## Meet the Team

### Coaching Staff
{% if coach %}
- **{{ coach.name }}** - {{ coach.position }}
  {% if coach.coaching_license %}*{{ coach.coaching_license }}*{% endif %}
  - *Joined: {{ coach.joined }}*
{% endif %}

### Players
{% for memberId in team.members %}
{% set member = members | findById(memberId) %}
{% if member %}
{% if member.role == "Player" %}

**{{ member.position }}**
- **{{ member.name }}**
  - *Joined: {{ member.joined }}*
  - *Born: {{ member.birth_date }}*

{% endif %}
{% endif %}
{% endfor %}

---

[← Back to Teams](/teams/)
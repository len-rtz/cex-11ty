---
title: "Team Details"
layout: base.njk
permalink: "/teams/team-002/"
teamId: "team-002"
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

### Team Members
{% for memberId in team.members %}
{% set member = members | findById(memberId) %}
{% if member %}
- **{{ member.name }}**{% if member.position %} - {{ member.position }}{% endif %}
  - *Role: {{ member.role }}*
  {% if member.joined %}*Joined: {{ member.joined }}*{% endif %}
  {% if member.birth_date %}*Born: {{ member.birth_date }}*{% endif %}
{% else %}
- **Member ID:** {{ memberId }} *(Details not available)*
{% endif %}
{% endfor %}

---

[← Back to Teams](/teams/)
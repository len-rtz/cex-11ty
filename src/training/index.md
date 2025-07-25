---
title: Training Schedule
layout: base.njk
---

# Training Schedule

<table>
  <thead>
    <tr>
      <th>Title</th>
      <th>Team</th>
      <th>Day</th>
      <th>Time</th>
      <th>Location</th>
      <th>Duration</th>
      <th>Coach</th>
      <th>Focus</th>
      <th>Equipment</th>
    </tr>
  </thead>
  <tbody>
    {% for session in training %}
      <tr>
        {% set team = teams | findById(session.team) %}
        {% set coach = members | findById(session.coach) %}
        <td>{{ session.title }}</td>
        <td>
          {% if team %}
            <a href="/teams/{{ team.id }}/">{{ team.name }}</a>
          {% else %}
            {{ session.team }}
          {% endif %}
        </td>
        <td>{{ session.day }}</td>
        <td>{{ session.time }}</td>
        <td>{{ session.location }}</td>
        <td>{{ session.duration }} min</td>
        <td>
          {% if coach %}
            {{ coach.name }}
          {% else %}
            {{ session.coach }}
          {% endif %}
        </td>
        <td>{{ session.focus }}</td>
        <td>{{ session.equipment | join(', ') }}</td>
      </tr>
    {% endfor %}
    {% if training | length == 0 %}
      <tr>
        <td colspan="9">No training at the moment.</td>
      </tr>
    {% endif %}
  </tbody>
</table>
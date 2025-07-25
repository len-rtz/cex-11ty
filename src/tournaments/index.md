---
title: Upcoming Tournaments
layout: base.njk
permalink: "/tournaments/"
---

# Upcoming Tournaments

<table>
  <thead>
    <tr>
      <th>Date</th>
      <th>Tournament</th>
      <th>Location</th>
      <th>Matchups</th>
    </tr>
  </thead>
  <tbody>
    {% for tournament in tournaments %}
    <tr>
      <td>{{ tournament.date }}</td>
      <td>{{ tournament.name }}</td>
      <td>{{ tournament.location }}</td>
      <td>
        {% for teamEntry in tournament.teams %}
        {% set team = teams | findById(teamEntry.id) %}
        {% if team %}
        <a href="/teams/{{ team.id }}/">{{ team.name }}</a> vs. {{ teamEntry.opponent }}
        {% if not loop.last %}<br>{% endif %}
        {% endif %}
        {% endfor %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>

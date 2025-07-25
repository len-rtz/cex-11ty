---
title: Upcoming Tournaments
layout: base.njk
permalink: "/tournaments/"
---

# Upcoming Tournaments

<!-- Debug info -->
<p>Debug: tournaments count = {{ tournaments | length }}</p>
<p>Debug: teams count = {{ teams | length }}</p>

<table border="1">
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
        DEBUG_START:
        {% for teamEntry in tournament.teams %}
          {% set team = teams | findById(teamEntry.id) %}
          Team ID: {{ teamEntry.id }} | 
          Found team: {{ team.name if team else 'NOT FOUND' }} | 
          Opponent: {{ teamEntry.opponent }}
          {% if not loop.last %}<br>{% endif %}
        {% endfor %}
        :DEBUG_END
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>

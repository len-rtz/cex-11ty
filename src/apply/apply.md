---
title: Membership Application
layout: base.njk
---

# Membership Application

<form method="post" action="#">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" required>

  <label for="team">Preferred Team:</label>
  <select id="team" name="team">
    {% for team in teams %}
      <option value="{{ team.id }}">{{ team.name }}</option>
    {% endfor %}
  </select>

  <button type="submit">Apply</button>
</form>
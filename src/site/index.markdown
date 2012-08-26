---
layout: default
---

<div class="hero-unit">
  <h1>Dart Facts</h1>
  <p>No opinion, just the facts, about the new structured web programming project.</p>
</div>

<ul>
{% for fact in site.pages %}
  {% if fact.url contains '/facts' %}
    <li>
    <a href="{{ fact.url }}">{{ fact.title }}</a>
    </li>
  {% endif %}
{% endfor %}
</ul>
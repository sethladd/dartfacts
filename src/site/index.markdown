---
layout: default
---

{% injectdata facts facts.yaml %}

<div class="hero-unit">
  <h1>Dart Facts</h1>
  <p>No opinion, just facts, about the new structured web programming project.</p>
</div>

{% for fact in page.facts %}
<section markdown="1">
## {{ fact[0] }}

{{ fact[1].desc }}
</section>
{% endfor %}
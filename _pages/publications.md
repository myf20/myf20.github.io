---
layout: page
permalink: /publications/
title: publications
description: List of selected publications
nav: true
---

<div class="publications">
  {% assign pubs = site.data.publications | group_by: "year" | sort: "name" | reverse %}

  {% for group in pubs %}
    <h2 class="year">{{ group.name }}</h2>
    {% for paper in group.items %}
      <div class="paper">
        <!--<span class="label">{{ paper.type }}</span>-->
        {% if paper.type %}
          <span class="pub-type">{{ paper.type }}</span>
        {% endif %}
        <!--<span class="label">{{ paper.type }}</span>-->
        <p>
          <strong>{{ paper.title }}</strong><br>
          {{ paper.authors }}<br>
          <em>{{ paper.conference }}</em><br>
          {% if paper.abstract %}
            <details><summary>Abstract</summary><p>{{ paper.abstract }}</p></details>
          {% endif %}
          {% if paper.pdf %}<a href="{{ paper.pdf }}" target="_blank">[PDF]</a>{% endif %}
          {% if paper.html %} <a href="{{ paper.html }}" target="_blank">[HTML]</a>{% endif %}
          {% if paper.doi %} <a href="https://doi.org/{{ paper.doi }}" target="_blank">[DOI]</a>{% endif %}
        </p>
      </div>
    {% endfor %}
  {% endfor %}
</div>
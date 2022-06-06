---
layout: default
permalink: /publications/
---

<h2> {{ site.data.rapt_site.pubsHeader }} </h2>

{% assign thisProject = site.data.rapt_site.project %}

{% assign citations = site.data.publications |  sort: "date" | reverse | group_by: "date" %}
{% for citation in citations %}
{% assign itemsSorted = citation.items | where: "project",thisProject %}

{% if itemsSorted.size > 0 %}
<h3>{{ citation.name }}</h3>
  <ul class="pubs">
  {% for item in itemsSorted %}<li>{{item.citation}}        
    {% for link in item.links %}
      {% if link.url %}<a href="{{link.url}}" target="_blank">[{{link.linklabel}}]</a>
      {% endif %}
    {% endfor %}
    </li>
  {% endfor %}
  </ul>
  {% endif %}
{% endfor %}



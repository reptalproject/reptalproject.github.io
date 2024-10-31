---
layout: default
permalink: /publications/
projectName: 'RepTal'

---

<h2> {{ site.data.rapt_site.pubsHeader }} </h2>

{% include filter_setup.html %}

{% assign thisProject = site.data.rapt_site.project %}

{% assign citations = site.data.rapt_web_data.publications |  sort: "date" | reverse | group_by: "date" %}
{% for citation in citations %}

{% assign itemsForProject = citation.items | where: "project", page.projectName %}
{% assign itemsForSecondaryProject = citation.items | where: "secondaryProject", page.projectName %}
{% assign filteredItemsForSecondaryProject = itemsForSecondaryProject | where_exp: "item", "item.secondaryProject != nil" %}
{% assign itemsCombined = itemsForProject | concat: filteredItemsForSecondaryProject | uniq %}
{% assign itemsSorted = itemsCombined | sort: "citation" %}

{% if itemsSorted.size > 0 %}
<h3>{{ citation.name }}</h3>
  <ul class="pubs">
  {% for item in itemsSorted %}<li class="pub-item" data-type="{{ item.type }}">{{item.citation}}        
    {% for link in item.links %}
      {% if link.url %}<a href="{{link.url}}" target="_blank"><i class="fa-regular fa-file-lines"></i>{{link.linklabel}}</a>
      {% endif %}
    {% endfor %}
    </li>
  {% endfor %}
  </ul>
  {% endif %}
{% endfor %}



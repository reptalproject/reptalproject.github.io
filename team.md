---
layout: default
permalink: /team/
---

## The RepTal Team

<div>
{% assign groups = site.data.members | group_by: "status" | sort: "value" %}
{% for group in groups %}

    <h3>{{ group.name }}{% if group.name != "Lab Alumni"%}s{%endif%}</h3>


    {% assign itemsSorted = group.items | sort: "last" %}

    {% for item in itemsSorted %}

        <div class="row">
        {% if item.pic %}
            <div class="thinLeft">
                <img src="{{item.pic}}" alt="Photo of {{item.name}}" width="100" >
            </div>
        {% else %}
            <div class="thinLeft">
                <img src="/assets/img/people/bee_icon.png" alt="Cute picture of a bee" width="100" >
            </div>
        {% endif %}
            <div class="right">
            <p>
                <strong>{{ item.first }} {{ item.last }}</strong> <em>{{ item.role }}</em><br>
                {% if item.affiliation %} {{ item.affiliation }}{% endif %}

                {% if item.url %}
                  <br><a href="{{ item.url }}" target="_blank">{{item.url}}</a>
                {% endif %}
            </p>

            </div>
        </div>
    {% endfor %}
    <br>

{% endfor %}
</div>

This page is being updated. Please contact Joshua at jdanish [at] indiana.edu if you want to now our current team.
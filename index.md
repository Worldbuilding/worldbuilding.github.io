---
title: "Index"
permalink: index.html
toc: false
---

{% for section in site.data.homenav.home_sections %}
## {{ section.heading }}

<div class="row">
    {% for item in section.items %}
    <div class="col-md-4 col-sm-6">
        <div class="panel panel-default nav-panel text-center">
            <div class="panel-heading">
                {% if item.image %}
                <img src="{{ site.baseurl }}/images/{{ item.image }}">
                {% else %}
                <span class="fa-stack fa-5x">
                      <i class="fas fa-circle fa-stack-2x text-primary"></i>
                      <i class="{{ item.icon }} fa-stack-1x fa-inverse"></i>
                </span>
                {% endif %}
            </div>
            <div class="panel-body">
                <h4 class="no-toc no-anchor">{{ item.title }}</h4>
                <p>{{ item.description }}</p>
                {% for button in item.buttons %}
                    {% if button.external_url %}
                    <a href="{{ button.external_url }}" class="btn btn-{{ button.category | default: "primary" }}">{{ button.title | default: "Visit" | append: " " }}</a>
                    {% else %}
                    <a href="{{ button.url | prepend: site.baseurl }}" class="btn btn-{{ button.category | default: "primary" }}">{{ button.title | default: "Visit" }}</a>
                    {% endif %}
                {% endfor %}
            </div>
         </div>
    </div>
    {% endfor %}
</div>
{% endfor %}

{% include links.html %}

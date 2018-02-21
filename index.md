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
        <div class="panel panel-default text-center">
            <div class="panel-heading">
                <span class="fa-stack fa-5x">
                      <i class="fas fa-circle fa-stack-2x text-primary"></i>
                      <i class="{{ item.icon }} fa-stack-1x fa-inverse"></i>
                </span>
            </div>
            <div class="panel-body">
                <h4>{{ item.title }}</h4>
                <p>{{ item.description }}</p>
                {% if item.external_url %}
                <a href="{{ item.external_url }}" class="btn btn-primary">{{ item.button | default: "Visit " }}</a>
                {% else %}
                <a href="{{ item.url | remove: "/" | prepend: site.baseurl }}" class="btn btn-primary">{{ item.button | default: "Visit " }}</a>
                {% endif %}
            </div>
         </div>
    </div>
    {% endfor %}
</div>
{% endfor %}

{% include links.html %}

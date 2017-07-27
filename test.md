---
layout: default
---

{% for tag in site.tags %}
    {% assign tagN = tag.first %}
    {% if tagN == page.tag %}
        {% assign tagP = tag.last %}
    {% endif %}
{% endfor %}
{% for post in tagP %}
    {% if post.title == page.title %}
        {% unless forloop.last %}
            {% assign next = tagP[forloop.index] %}
            <li class="previous">
            <a href="{{ site.baseurl }}{{ next.url }}">&larr;{{ next.title }}</a>
            </li>
        {% endunless %}
        {% unless forloop.first %}
            <li class="next">
            <a href="{{ site.baseurl }}{{ prev.url }}">{{ prev.title }}&rarr;</a>
            </li>
        {% endunless %}
    {% endif %}
    {% assign prev = post %}
{% endfor %}

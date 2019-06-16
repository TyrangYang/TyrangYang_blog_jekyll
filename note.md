---
layout: page
permalink: /note/
title: Self study note
---

{% for post in site.posts %}
{% if post.categories contains "note" %}
## [{{post.title}}]({{site.url}}{{ site.baseurl }}{{post.url}})
{{ post.date | date_to_string }}
{% endif %}
{% endfor %}

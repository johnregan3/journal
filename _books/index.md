---
layout: page
title: Books
weight: 1
tags: [archive]
---
{% assign items = site.books | sort: 'weight' %}

{% include description-books.html %}

See also <a href="/tags-book/" title="Book Tags">Book Tags</a> and <a href="/tags-people/" title="People Tags">People Tags</a>.

## All Book Notes

{% for item in items %}
{% if item.tags contains 'single book' %}
<h3 class="list-title"><a href="{{item.url}}">{{item.title}}</a></h3>
<ul class="no-bullets">
{% for chapter in items %}
{% if chapter.tags contains 'single chapter' and chapter.book_name contains item.title %}
<li><a href="{{chapter.url}}">{{chapter.title}}</a>
<ul>
{% for passage in items %}
{% if passage.tags contains 'passage' and passage.chapter_name contains chapter.title %}
<li><a href="{{passage.url}}">{{passage.title}}</a></li>
{% endif %}
{% endfor %}
</ul>
</li>
{% endif %}
{% endfor %}
</ul>
{% endif %}
{% endfor %}


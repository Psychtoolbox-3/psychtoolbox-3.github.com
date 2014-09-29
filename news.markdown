---
layout: default
---

Psychtoolbox News
-----------------

{% for post in site.posts %}
<article class="post">
    <header>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>
        <a href="http://github.com/{{ post.author }}" class="author">{{ post.author }}</a>
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: '%B %d, %Y' }}</time>
      </p>
    </header>

    {{ post.content }}

</article>
{% endfor %}

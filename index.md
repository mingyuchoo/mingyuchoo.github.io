## Welcome to Mingyu Choo's GitHub Pages

Hello?
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </li>
  {% endfor %}
</ul>

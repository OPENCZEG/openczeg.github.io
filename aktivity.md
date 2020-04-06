---
title: Naše aktivity
layout: page
subtitle: Co jsme pro vás v rámci #openczeg připravili a co chystáme...
order: 5
---

{% for aktivita in site.aktivity %}
  <h2>{{ aktivita.title }} </h2>
<p>Popis: {{aktivita.subtitle}}<p>
<p>Stav: {{aktivita.stav}}</p>
<p>URL odkaz: <a href="{{aktivita.link}}">{{aktivita.link}}</a>
<p>{{ aktivita.content | markdownify }}</p>
{% endfor %}
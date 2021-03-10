---
layout: page
current: archive
title: 태그로 선택해서 보자!
navigation: true
logo: 
class: page-template
subclass: 'post page'
---

<div id="post-index" class="well article">
{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tags_list = site_tags | split:',' | sort %}

<ul class="entry-meta inline-list">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
  	<li><a href="#{{ this_word }}" class="tag"><span class="term alltags">{{ this_word }}</span> <span class="count alltags">{{ site.tags[this_word].size }}</span></a></li>
  {% endunless %}{% endfor %}
</ul>

{% for item in (0..site.tags.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
	<article>
	<!--각 태그명-->
	<h3 id="{{ this_word }}" class="tag">{{ this_word | upcase }}</h3>
        <!--태그별 글 리스트-->
        <ul>	        
            {% for post in site.tags[this_word] %}{% if post.title != null %}
              <!--각 글 li 시작-->  
              <li class="entry-title">
                <a href="{{ post.url }}" target="_self" title="{{ post.title }}">
                <h6>{% if post.author == "tingstyle1" %}🧑🏻{% else %}👧🏻{% endif %}{{ post.date | date: '%Y-%m-%d' }}  {{ post.title }}</h6>  
                </a>
            </li>
            {% endif %}{% endfor %}
        </ul>
	</article><!-- /.hentry -->
{% endunless %}{% endfor %}
</div>
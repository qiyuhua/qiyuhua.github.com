---
layout: landing
title: 齐玉华的个人博客
head_title: 玉怜其华
description: |
  科大的升华人生
---

<div class="row" style="margin-bottom:20px;">
  <div style="width:100%">
    <h3 style="margin-bottom:5px; margin-left:20px; color:#333333; padding-top:25px;">我们需要与众不同。我们本来就与众不同。</h3>
    <h6 align="right" style="font-size:12px; margin-right:8px">喜欢我或者我的博客，可以把它加入你的<a href="javascript:void(0)" onclick="window.external.AddFavorite(location.href, document.title)">收藏夹</a></h6>
  </div>
  <div class="divbox" style="width:96%;margin-right:0px;padding-right:10px;">
    <h1 id="start-now" style="margin-left: 0px; margin-right: 0px; font-size: 22px;">最新博文</h1>
    <div style="margin-left:-15px">
    {% assign posts_all = site.posts %}
    {% if posts_all.size > 5 %}{% comment %} 在首页显示posts个数设定 {% endcomment %}
    	{% assign count = 5 %}
    {% else %}
	{% assign count = posts_all.size %}
    {% endif %}
    {% include custom/posts_all %}
  </div>
  </div>
  
</div>


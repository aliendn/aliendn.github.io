---
layout: page
title: About
permalink: /about/
weight: 3
---

# **{{ site.author.name }} resume**

<img class="about_img_personal" src="/images/personal.png" />


Hi I am **{{ site.author.name }}** :wave:,<br>

Junior programmer front-end & back-end Work experience in the field of startups and cooperation and high experience in team work in designing corporate and store sites using Django framework and API using fastapi & drf and the latest Developed tools fluent in English (experience of two years of living and studying in Hungary) as well as fluent in Linux and Python by taking the best in-person and online courses at boot camps and schools and offline training sites. I am excited to learn more and more.

* * *

<div class="row">
{% include about/skills.html title="Programming Skills" source=site.data.programming-skills %}
{% include about/skills.html title="Other Skills" source=site.data.other-skills %}
</div>

* * *

<div class="row">
{% include about/timeline.html %}
</div>

* * *

<br/>
<h4>license and courses</h4>

<div class="row">
{% include about/courses.html %}
</div>

* * *

<br/>
<h5 class="section-title h1">Main Projects</h5>

<section>
  <div class="container py-5">
    <div class="row">
      <div class="col-md-12">
        <div class="main-timeline">
          {% include about/exprience.html %}
        </div>
        </div>
    </div>
  </div>
</section>
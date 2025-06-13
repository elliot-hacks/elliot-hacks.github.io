---
layout: home
title: Home
permalink: /
---

<!-- About Section -->
<section class="py-5 border-bottom wow fadeInUp" data-wow-delay="0.1s">
  <h1 class="title pb-3 mb-5">About Me</h1>
  <p>{{ site.description }}</p>
  
  <div class="row mb-4">
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Name:</span> {{ site.author.name }}
    </div>
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Github:</span> <a href="https://github.com/elliot-hacks"> @elliot-hacks</a>
    </div>
    <!-- Add other details similarly -->
  </div>
</section>

<!-- Skills Section -->
<section class="py-5 border-bottom wow fadeInUp" data-wow-delay="0.1s">
  <h1 class="title pb-3 mb-5">Technical Skills</h1>
  <div class="row">
    {% for skill_group in site.data.skills %}
    <div class="col-sm-6">
      <h4 class="mb-3">{{ skill_group.category }}:</h4>
      {% for skill in skill_group.items %}
      <div class="skill mb-4">
        <div class="d-flex justify-content-between">
          <p class="mb-2">{{ skill.name }}</p>
          <p class="mb-2">{{ skill.percentage }}%</p>
        </div>
        <div class="progress">
          <div class="progress-bar bg-primary" role="progressbar" style="width: {{ skill.percentage }}%;" 
               aria-valuenow="{{ skill.percentage }}" aria-valuemin="0" aria-valuemax="100"></div>
        </div>
      </div>
      {% endfor %}
    </div>
    {% endfor %}
  </div>
</section>

<!-- Include other sections similarly -->
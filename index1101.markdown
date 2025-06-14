---
layout: home
title: "Let's Talk Security"
permalink: /
---

<main style="padding: 20px; position: sticky; top: 0">
  <h1>Greeting fellow Technology Enthusiasts</h1>
  <p>Let's talk Security!</p>
</main>

<!-- About Section -->
<section class="py-5 border-bottom wow fadeInUp" data-wow-delay="0.1s">
  <h1 class="title pb-3 mb-5">About Me</h1>
  <p>{{ site.description }}</p>
  
  <div class="row mb-4">
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Name:</span> {{ site.author.name }}
    </div>
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Github:</span> <a href="{{ site.author.github_url }}"> {{ site.author.github }}</a>
    </div>
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Degree:</span> {{ site.author.degree }}
    </div>
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Experience:</span> {{ site.author.experience }}
    </div>
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Email:</span> {{ site.author.email }}
    </div>
    <div class="col-sm-6 py-1">
      <span class="fw-medium text-primary">Location:</span> {{ site.author.location }}
    </div>
  </div>
  
  <div class="row g-4">
    {% for stat in site.author.stats %}
    <div class="col-md-4 col-lg-6 col-xl-4">
      <div class="d-flex bg-secondary p-4">
        <h1 class="flex-shrink-0 display-5 text-primary mb-0" data-toggle="counter-up">{{ stat.value }}</h1>
        {% if stat.plus %}<h1 class="flex-shrink-0 display-5 text-primary mb-0">+</h1>{% endif %}
        <div class="ps-3">
          <p class="mb-0">{{ stat.label }}</p>
          <h5 class="mb-0">{{ stat.subtitle }}</h5>
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
</section>

{% include sections/skills.html %}
{% include sections/experience.html %}
{% include sections/projects.html %}
{% include sections/publications.html %}
{% include sections/contact.html %}
---
layout: page
title: Portfolio
permalink: /portfolio/
description: "Portfolio of George Nyakundi — tech projects and music releases. iOS apps, EPs, and collaborations as Agani Nyakundi."
---

<div class="portfolio-filters" role="group" aria-label="Filter by category">
  <button type="button" class="portfolio-pill portfolio-pill-active" data-filter="all">All</button>
  <button type="button" class="portfolio-pill" data-filter="tech">Tech</button>
  <button type="button" class="portfolio-pill" data-filter="music">Music</button>
</div>

<p class="portfolio-intro">Tech and music projects.</p>

<div class="portfolio-grid">
  {% assign portfolio_pages = site.pages | where: "portfolio_project", true | sort: "sort_order" %}
  {% for project in portfolio_pages %}
  <a href="{{ project.url | relative_url }}" class="portfolio-card portfolio-card-{{ project.category | default: 'tech' }}" data-category="{{ project.category | default: 'tech' }}">
    <div class="portfolio-card-image">
      {% if project.thumbnail %}
      <img src="{{ project.thumbnail | relative_url }}" alt="{{ project.title }}">
      {% else %}
      <div class="portfolio-card-placeholder">
        <span class="portfolio-card-placeholder-icon" aria-hidden="true">♪</span>
        <span class="portfolio-card-placeholder-label">{{ project.category | default: 'Music' }}</span>
      </div>
      {% endif %}
    </div>
    <div class="portfolio-card-content">
      <span class="portfolio-card-tag">{{ project.category | default: 'Tech' }}</span>
      <h3 class="portfolio-card-title">{{ project.title }}</h3>
      <p class="portfolio-card-meta">{{ project.meta }}</p>
      <p class="portfolio-card-excerpt">{{ project.excerpt }}</p>
    </div>
  </a>
  {% endfor %}
</div>

<p class="portfolio-footer"><em>More projects coming soon. <a href="https://www.linkedin.com/in/{{ site.linkedin_username }}">Connect on LinkedIn</a> to discuss my experience.</em></p>

<script>
(function() {
  var pills = document.querySelectorAll('.portfolio-pill');
  var cards = document.querySelectorAll('.portfolio-card');
  if (!pills.length || !cards.length) return;
  pills.forEach(function(pill) {
    pill.addEventListener('click', function() {
      var filter = this.getAttribute('data-filter');
      pills.forEach(function(p) { p.classList.remove('portfolio-pill-active'); });
      this.classList.add('portfolio-pill-active');
      cards.forEach(function(card) {
        var cat = card.getAttribute('data-category');
        if (filter === 'all' || cat === filter) {
          card.classList.remove('portfolio-card-hidden');
        } else {
          card.classList.add('portfolio-card-hidden');
        }
      });
    });
  });
})();
</script>

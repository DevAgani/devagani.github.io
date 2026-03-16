---
layout: home
list_title: "Writing"
title: "George Nyakundi — Senior iOS Engineer"
description: "Senior iOS Engineer at eBay. 10+ years building fintech & mobile products. Based in the Netherlands. Open to collaboration and opportunities."
---

<section class="home-hero">
  <p class="home-role">iOS Software Engineer at <strong>eBay</strong></p>
  <p class="home-tagline">Building fintech & mobile products. Based in the Netherlands. Open to collaboration and opportunities.</p>
  <p class="home-beyond">Engineering · Music · Running</p>
  <p class="home-beyond-note">Singer, guitarist — <a href="https://open.spotify.com/search/Agani%20Nyakundi" target="_blank" rel="noopener noreferrer">Agani Nyakundi on Spotify</a> · 8× half-marathoner</p>
</section>

<section class="home-featured">
  <h2 class="home-section-heading">Featured work</h2>
  <div class="home-project-grid">
    {% assign portfolio_pages = site.pages | where: "featured", true | sort: "sort_order" %}
    {% for project in portfolio_pages %}
    <a href="{{ project.url | relative_url }}" class="home-project-card">
      <div class="home-project-image">
        {% if project.thumbnail %}
        <img src="{{ project.thumbnail | relative_url }}" alt="{{ project.title }}">
        {% else %}
        <div class="home-project-placeholder">
          <span aria-hidden="true">♪</span>
          <span>{{ project.category | default: 'Music' | capitalize }}</span>
        </div>
        {% endif %}
      </div>
      <div class="home-project-content">
        <span class="home-project-tag">{{ project.category | default: 'Tech' | capitalize }}</span>
        <h3 class="home-project-title">{{ project.title }}</h3>
        {% if project.meta %}<p class="home-project-meta">{{ project.meta }}</p>{% endif %}
        {% if project.excerpt %}<p class="home-project-excerpt">{{ project.excerpt }}</p>{% endif %}
      </div>
    </a>
    {% endfor %}
  </div>
  <p class="home-featured-footer"><a href="{{ '/portfolio/' | relative_url }}">View all projects →</a></p>
</section>

---
layout: default
title: Entries
permalink: /entries/
---

<div class="prose">
  <h1>Entries</h1>

  <p>
    ProofZoom entries are concise expository articles organized by area and subarea.
    Each entry is available in web form for online reading and, where provided, as a PDF for download and offline use.
  </p>

  {% assign pz_sorted_entries = site.entries | sort: "entry_id" %}

  {% for entry in pz_sorted_entries %}
    <article class="entry-listing">

      <h2 class="entry-listing-title">
        <a href="{{ entry.url | relative_url }}">
          {{ entry.entry_id | upcase }} — {{ entry.title }}
        </a>
      </h2>

      {% if entry.abstract %}
        <p class="entry-listing-abstract">
          {{ entry.abstract }}
        </p>
      {% endif %}

      <p class="entry-listing-meta">
        {% if entry.primary_area %}<span>Area: {{ entry.primary_area }}</span>{% endif %}
        {% if entry.primary_subarea %}<span> • Subarea: {{ entry.primary_subarea }}</span>{% endif %}
        {% if entry.difficulty %}<span> • Difficulty: {{ entry.difficulty }}</span>{% endif %}
        {% if entry.status %}<span> • Status: {{ entry.status }}</span>{% endif %}
        {% if entry.updated %}<span> • Updated: {{ entry.updated }}</span>{% endif %}
      </p>

      {% if entry.pdf %}
        <p class="entry-listing-pdf">
          <a href="{{ entry.pdf | relative_url }}" download>
            Download PDF
          </a>
        </p>
      {% endif %}

      {% unless forloop.last %}
        <hr class="hr">
      {% endunless %}

    </article>
  {% endfor %}
</div>
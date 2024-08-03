---
title: "Research Projects"
date: 2024-08-01
draft: false
---

# Research Projects

Welcome to the Research Projects section. Here you can find a list of my projects with a brief description and a sneak peek.

{{ range .Pages }}
  <div class="project-preview">
    <a href="{{ .RelPermalink }}">
      <img src="{{ .Params.image }}" alt="{{ .Title }}" class="project-image">
      <h2>{{ .Title }}</h2>
      <p>{{ .Params.description }}</p>
    </a>
  </div>
{{ end }}

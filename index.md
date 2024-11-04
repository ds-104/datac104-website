---
layout: home
nav_order: 0
---

{%- if site.under_construction -%}
<p class="warning">
This site is under construction. All dates and policies are tentative until this message goes away.
</p>
{%- endif -%}

<!--<p class="warning">
If you're currently on the waitlist, or have any other course-related logistics questions, please take a look at our <a href="{{ site.baseurl }}/resources/faqs">Course FAQs</a> prior to contacting course staff.
</p>-->

<img align="right" alt="161 lock logo" width="85px" src="{{ site.baseurl }}/assets/images/logo.png">

# {{ site.title }}

<strong>Instructor</strong>: Name / <strong>Lecture</strong>: Date Time, Location [Zoom, Playlist]

## Course Calendar

[Skip to current week](#week-{{ 'now' | date: '%U' }}){: .btn .btn-outline .fs-3 }

<div>
{%- include syllabus.html -%}
</div>

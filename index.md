---
layout: home
title: Schedule
nav_order: 0
---

{%- assign instructors = site.staffers | where: 'role', 'Instructor' | map: "name" -%}
{%- assign instructor_msg = "Instructor" -%}
{%- if instructors.size != 1 -%}
{%- assign instructor_msg = "Instructors" -%}
{%- endif -%}

{%- if site.under_construction -%}
<p class="warning">
This site is under construction. Further, all dates and policies apply to the Fall 2024 offering of Data C104 only.
</p>
{%- endif -%}

{%- if site.waitlist_warning -%}
<p class="warning">
If you're currently on the waitlist, or have any other course-related logistics questions, please take a look at our <a href="{{ site.baseurl }}/resources/faqs">Course FAQs</a> prior to contacting course staff.
</p>
{%- endif -%}

{%- if site.outdated -%}
<p class="warning">
This website contains materials from a past semester. Information, assignments, and announcements may no longer be relevant. Please refer to the <a href="https://template.cs161.org">current semester's site</a> for up-to-date content.
</p>
{%- endif -%}


<!-- <img align="right" alt="Data C104 logo" width="160px" src="{{ site.baseurl }}/assets/images/logo.png"> -->

# {{ site.title }}

{% if site.semester != empty %}
<span style="white-space: nowrap;">
    <strong>Semester</strong>: {{ site.semester }}
    <br>
</span>
{% endif -%}
{%- if instructors.size != 0 -%}
<span>
    <strong>{{instructor_msg}}</strong>: {{ instructors | join: ", " }}{%- if site.lecture.time != "" %} {%- endif -%}
    <br>
</span>
{% endif -%}
{%- if site.lecture.time != empty -%}
<span style="white-space: nowrap;">
    <strong>Lecture</strong>: {{ site.lecture.time }}
    {%- if site.lecture.location.name != empty and site.lecture.location.link != empty -%}
    , [{{site.lecture.location.name}}]({{site.lecture.location.link}})
    {%- elsif site.lecture.location.name != empty -%}
    , {{site.lecture.location.name}}
    {%- endif -%}
</span>
{% endif -%}


<!-- {%- if site.heading_links.size != 0 -%}
<span style="white-space: nowrap;">
    [
    {%- for link in site.heading_links -%}
    {%- unless forloop.first -%}, {% endunless -%}
    {%- if link.text != empty and link.url != empty -%}
    [{{link.text}}]({{link.url}})
    {%- elsif link.text != empty -%}
    {{link.text}}
    {%- endif -%}
    {%- endfor -%}
    ]
</span>
{% endif -%} -->

**Why this course?** Data-driven analytics and artificial intelligence-powered devices now shape innumerable aspects of our lives. Beneath the surface of these technologies, computational and increasingly autonomous techniques that operate on large, ever-evolving datasets are transforming how people act in and know the world. These new analytic tools, algorithmic systems, and computational infrastructures draw from and reconstruct existing societal structures, patterns, and narratives. Sometimes this is obvious, and sometimes it is invisibly so. Data technologies have profound consequences for how we think of ourselves, relate to one another, organize collective life, and envision desirable futures. This course helps you identify and analyze these human stakes, reason about them with others, and shape opportunities to take action toward outcomes that can serve collective well-being.

**If you intend to major or minor in Data Science,** the course meets the Human Contexts and Ethics (HCE) requirement of Berkeley’s Data Science program. It gives you systematic exposure and reflective practice in engaging with the human actions, decisions, and social structures that intrinsically shape your work.

**If you don’t intend to major or minor in Data Science,** the course will jumpstart your knowledge and strengthen your capacity to take part in guiding our datafied world. The course carries the broad, inclusive spirit of Berkeley’s Data Science curriculum into the area of human society and collective world-making.

**Breadth Requirements:** This class has been approved for breadth in Philosophy & Values and Historical Studies and the EECS/LSCS Ethics requirement.

**STS Minor:** This class counts as an upper-division elective for the undergraduate minor in Science, Technology, and Society.

## Scope and Objectives

How do we shape action together in our complex and changing datafied world, aiming at outcomes that improve the human condition? To help you on this path, this course provides an overall introduction to how data science and data technologies -- including data analytics, algorithmic decision systems, machine learning (ML), and artificial intelligence (AI) -- are entangled today with diverse human contexts (histories, institutions, and material bases) and ethics (domains of moral action, collective world-making, and justice).

We will bring historically-grounded perspectives, frameworks from Science, Technology, and Society (STS), and approaches from other disciplines in the humanities and interpretive social sciences to bear on topics that include:

* Doing ethical data science amid shifting definitions of human subjects, consent, and privacy;
* Understanding representation, power shifts, and justice in data-enabled technologies, including predictive analytics, precision (targeted) services, and surveillance technologies;
* Contemporary landscapes of labor and industry; and
* The changing relationship between data, democracy, and public life.

The course aims, first of all, to prepare you to recognize when, where, and how data, analytics, and associated technologies shape and govern the human condition. Further, it aims to provide you with a toolkit with which to think critically about human contexts and ethics issues of data science and data technologies when you encounter them in routine work or daily life, to influence how data science is used to achieve better outcomes for people, and to be able to articulate (for yourself, and to others) what “better” means.


## Course Calendar

<div>
{%- include syllabus.html -%}
</div>

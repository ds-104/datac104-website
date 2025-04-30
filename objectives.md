---
layout: page
title: Learning Objectives
nav_order: 3
description: >-
    Learning goals for the course.
---


{%- if site.under_construction -%}
<p class="warning">
This site is under construction. All dates and policies are tentative until this message goes away.
</p>
{%- endif -%}

{%- if site.outdated -%}
<p class="warning">
This website contains materials from a past semester. Information, assignments, and announcements may no longer be relevant. Please refer to the <a href="https://template.cs161.org">current semester's site</a> for up-to-date content.
</p>
{%- endif -%}

{%- comment -%}
- This file auto-generates the syllabus with all the days of the semester.
- You should not need to touch anything in here unless you're rewriting
the website; all configuration variables can be changed in the _data folder.
{%- endcomment -%}

{%- comment -%}
- Create a list, valid_dates, with a list of all days we want to appear on the schedule.
- Uses Unix time to calculate days, because Jekyll is weird.
- Use start_date, end_date, and class_days in syllabus.yml to control this.
{%- endcomment -%}
{%- assign start_epoch = site.data.syllabus.start_date | date: '%s' -%}
{%- assign end_epoch = site.data.syllabus.end_date | date: '%s' -%}
{%- assign seconds_in_day = 60 | times: 60 | times: 24 -%}
{%- assign start_days_epoch = start_epoch | divided_by: seconds_in_day -%}
{%- assign end_days_epoch = end_epoch | divided_by: seconds_in_day -%}
{%- assign valid_dates = "" | split: "" -%}
{%- for days_epoch in (start_days_epoch..end_days_epoch)-%}
{%- assign date = days_epoch | times: seconds_in_day -%}
{%- assign day_of_week = date | date: '%w' -%}
{%- if site.data.syllabus.class_days contains day_of_week -%}
{%- assign valid_dates = valid_dates | push: date -%}
{%- endif -%}
{%- endfor -%}

{%- comment -%}
- Manually add any extra days we need to appear on the schedule.
- Use extra_days in syllabus.yml to control this.
{%- endcomment -%}
{%- for item in site.data.syllabus.extra_days -%}
{%- assign extra_day_epoch = item.date | date: '%s' | plus: 0 -%}
{%- assign valid_dates = valid_dates | push: extra_day_epoch -%}
{%- endfor -%}

{%- comment -%}
Sort days and group into weeks.
sorted_dates is an array, where each element is a hash with three fields:
- "name" is the week number (between 1 and 52)
- "items" is an array of days we'll display in that week (in Unix time)
- "size" is the number of days we'll display in that week
{%- endcomment -%}
{%- assign sorted_dates = valid_dates | sort | group_by_exp: "it", "it | date: '%U'" -%}

# Learning Objectives

<div>
  <table>
    {%- comment -%}
    - Table header.
    - Use syllabus.yml to change table widths.
    {%- endcomment -%}
    <thead>
    <th style="width:{{ site.data.syllabus.unit_width }}">Unit</th>
    <th style="width:{{ site.data.syllabus.date_width }}">Week</th>
    <th style="width:{{ site.data.syllabus.objective_width }}">Learning Objectives</th>
    </thead>

    {%- comment -%}
    Table body.
    - Fill in assignment names/links in lecture.yml, readings.yml,
    discussion.yml, homework.yml, and project.yml, not here.
    - In this code, we have five categories: lecture, discussion, readings,
    homework, and project. The code for rendering each column here
    is identical; the code for filling in the content of each column
    can be found in lecture.html, readings.html, discussion.html,
    homework.html, and project.html.
    - For each category/column, we keep track of three counters, which
    are described below.
    {%- endcomment -%}
    <tbody>

    {%- comment -%}
    - Initialize the index counters.
    - This indicates the next element in the yml array to be rendered.
    - You should not need to change or care about these.
    {%- endcomment -%}
    {%- assign lecture_index = 0 -%}
    {%- assign discussion_index = 0 -%}
    {%- assign homework_index = 0 -%}
    {%- assign project_index = 0 -%}
    {%- assign week_index = 0 -%}

    {%- assign objectives_index = 0 -%}

    {%- comment -%}
    - Initialize the rowspan counters.
    - For multi-row boxes (e.g. projects that span several weeks), we need to keep
    track of how many rows we need to skip before rendering another box.
    - You should not need to change or care about these.
    {%- endcomment -%}
    {%- assign lecture_rowspan = 0 -%}
    {%- assign discussion_rowspan = 0 -%}
    {%- assign homework_rowspan = 0 -%}
    {%- assign project_rowspan = 0 -%}
    {%- assign week_rowspan = 0 -%}


    {%- assign objectives_rowspan = 3 -%}

    {%- comment -%}
    - Initialize the number counters.
    - Each category/column contains a numbered list, and we automatically
    count upwards in this code. (For example, the lecture numbers are
    automatically generated in this code.)
    - Because not all elements in the yml array need to be numbered
    (e.g. "no lecture" days shouldn't add to the lecture number),
    the number ends up being different from the index counter above.
    - You can adjust the starting number (e.g. should we start at HW0 or
    HW1?) by editing the starting_number config variables in syllabus.yml.
    {%- endcomment -%}
    {%- assign lecture_number = site.data.syllabus.starting_lecture_number -%}
    {%- assign discussion_number = site.data.syllabus.starting_discussion_number -%}
    {%- assign homework_number = site.data.syllabus.starting_homework_number -%}
    {%- assign project_number = site.data.syllabus.starting_project_number -%}
    {%- assign default_week_rowspan = site.data.syllabus.default_week_rowspan -%}

    {%- comment -%}
    - These are the default rowspans we assume if you don't provide one in
    the yml file.
    - See syllabus.yml for more information on what these are, and to modify them.
    {%- endcomment -%}
    {%- assign default_lecture_rowspan = site.data.syllabus.default_lecture_rowspan -%}
    {%- assign default_discussion_rowspan = site.data.syllabus.default_discussion_rowspan -%}
    {%- assign default_homework_rowspan = site.data.syllabus.default_homework_rowspan -%}
    {%- assign default_project_rowspan = site.data.syllabus.default_project_rowspan -%}
    {%- assign default_objectives_rowspan = site.data.syllabus.default_objectives_rowspan -%}

    {%- for week in sorted_dates -%}

    {%- comment -%}
    - Since our for loop is iterating through weeks, we'll use the for
    loop's index to figure out which week we're in.
    - In Jekyll, forloop.index0 starts counting at 0, and forloop.index
    starts counting at 1. We use forloop.index0 if we want to count
    starting with Week 0, and forloop.index if we want to count starting
    with Week 1.
    - You can adjust whether the first week of class is Week 0 or Week 1
    by editing starting_week_number in syllabus.yml.
    {%- endcomment -%}
    {%- if site.data.syllabus.starting_week_number == '0' -%}
    {%- assign week_number = forloop.index0 -%}
    {%- else -%}
    {%- assign week_number = forloop.index -%}
    {%- endif -%}


    {%- comment -%}
    - This is how we get alternating colors per week.
    - This code is tied to the loop iterating through weeks, so we can
    currently only support alternating colors per week.
    - To change the shading color, edit td.is-even in _sass/custom/custom.scss.
    - The first week is light-colored. If you absolutely must make the first
    week shaded, change forloop.index to forloop.index0 just below this line.
    {%- endcomment -%}
    {%- assign is_even_mod = forloop.index | modulo:2 -%}
    {%- if is_even_mod == 0 -%}
    {%- assign is_even = "is-even" -%}
    {%- else -%}
    {%- assign is_even = "" -%}
    {%- endif -%}

    {%- comment -%}
    - In a given week, iterate through all the days in that week.
    {%- endcomment -%}
    {%- for day in week.items -%}
    <tr>
      {%- comment -%}
      - Render the project column.
      - For simplicity, the code for each column should be kept identical (only
      swapping out the column names.
      {%- endcomment -%}
      {%- if project_rowspan == 0 -%}
      {%- assign project_element = site.data.projects.projects[project_index] -%}
      {%- if project_element.rowspan -%}
      {%- assign new_rowspan = project_element.rowspan -%}
      {%- else -%}
      {%- assign new_rowspan = default_project_rowspan -%}
      {%- endif -%}
      {%- include project.html element=project_element number=project_number rowspan=new_rowspan is_even=is_even  -%}
      {%- assign project_rowspan = new_rowspan | plus:-1 -%}
      {%- assign project_index = project_index | plus:1 -%}
      {%- unless project_element.nonumber -%}
      {%- assign project_number = project_number | plus:1 -%}
      {%- endunless -%}
      {%- else -%}
      {%- assign project_rowspan = project_rowspan | plus:-1 -%}
      {%- endif -%}

      {%- if week_rowspan == 0 -%}
      {%- assign week_element = site.data.week.weeks[week_index] -%}
      {%- if week_element.rowspan -%}
      {%- assign new_rowspan = week_element.rowspan -%}
      {%- else -%}
      {%- assign new_rowspan = default_week_rowspan -%}
      {%- endif -%}
      {%- include discussion.html element=week_element rowspan=new_rowspan is_even=is_even -%}
      {%- assign week_rowspan = new_rowspan | plus:-1 -%}
      {%- assign week_index = week_index | plus:1 -%}
      {%- unless week_element.nonumber -%}
      {%- assign week_number = week_number | plus:1 -%}
      {%- endunless -%}
      {%- else -%}
      {%- assign week_rowspan = week_rowspan | plus:-1 -%}
      {%- endif -%}
      
      {%- comment -%}
       - Render the discussion column.
       - For simplicity, the code for each column should be kept identical (only
       swapping out the column names.
       {%- endcomment -%}
       {%- if discussion_rowspan == 0 -%}
       {%- assign discussion_element = site.data.objectives.objectives[discussion_index] -%}
       {%- if discussion_element.rowspan -%}
       {%- assign new_rowspan = discussion_element.rowspan -%}
       {%- else -%}
       {%- assign new_rowspan = default_discussion_rowspan -%}
       {%- endif -%}
       {%- include discussion.html element=discussion_element number=discussion_number rowspan=new_rowspan is_even=is_even -%}
       {%- assign discussion_rowspan = new_rowspan | plus:-1 -%}
       {%- assign discussion_index = discussion_index | plus:1 -%}
       {%- unless discussion_element.nonumber -%}
       {%- assign discussion_number = discussion_number | plus:1 -%}
       {%- endunless -%}
       {%- else -%}
       {%- assign discussion_rowspan = discussion_rowspan | plus:-1 -%}
       {%- endif -%}

    </tr>
    {%- endfor -%}
    {%- endfor -%}
    </tbody>
  </table>
</div>
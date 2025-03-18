---
layout: page
permalink: /publications/
title: publications
description: Selected publications from Sonic Intangibles and its team members
nav: true
nav_order: 2
---

<!-- _pages/publications.md -->
<div class="publications">

{% bibliography --query @*[keywords ^= list]* %}

</div>

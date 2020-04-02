---
layout: post
---
{{ content }}

<!-- more -->

<div class="meta-container">
    {% if page.total_time %}
        <div class="meta">
            <h3>Time</h3>
            <div class="content">
                {{ page.total_time }} total<br>
                <em>{{ page.active_time }} active</em><br>
                <em>{{ page.inactive_time }} inactive</em>
            </div>
        </div>
    {% endif %}
    {% if page.difficulty %}
        <div class="meta">
            <h3>Difficulty</h3>
            <h4 class="content">{{ page.difficulty }}</h4>
        </div>
    {% endif %}
    <div class="meta print-recipe">
        <h3>Print</h3>
        <div class="content center">
            <a href="javascript:window.print();">
                <i class="fa fa-print"></i>
            </a>
        </div>
    </div>
</div>

<div class="recipe-container">
    <div class="equipment-ingredients">
        <h2>Equipment</h2>
        <ul>
            {% for item in page.equipment %}
                <li>{{ item|liquify|markdownify }}</li>
            {% endfor %}
        </ul>
        <hr>
        <h2>Ingredients</h2>
        <ul>
            {% for ingredient in page.ingredients %}
                <li><strong>{{ ingredient[1] }}</strong> {{ ingredient[0] }}</li>
            {% endfor %}
        </ul>
        <hr class="mobile-only-hr">
    </div>
    <div class="directions">
        <h2>Directions</h2>
        <ol>
            {% for direction in page.directions %}
                <li>{{ direction|liquify|markdownify }}</li>
            {% endfor %}
        </ol>
    </div>
    <div class="notes">
        <hr>
        <h2>Notes</h2>
        <ul>
            {% for note in page.notes %}
                <li><p>{{ note|liquify|markdownify }}</p></li>
            {% endfor %}
        </ul>       
    </div>
</div>
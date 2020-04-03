---
layout: post
---
{{ content }}

<!-- more -->

<div class="meta-container">
    {% if page.total_time %}
        <div class="meta">
            <h3><i class="fa fa-clock-o"></i> Time</h3>
            <div class="content">
                {{ page.total_time }} total<br>
                <em>{{ page.active_time }} active</em>
            </div>
        </div>
    {% endif %}
    {% if page.difficulty %}
        <div class="meta">
            <h3><i class="fa fa-cogs"></i> Difficulty</h3>
            <h4 class="content">{{ page.difficulty }}</h4>
        </div>
    {% endif %}
    {% if page.output %}
        <div class="meta">
            <h3><i class="fa fa-cubes"></i> Output</h3>
            <h4 class="content">{{ page.output }}</h4>
        </div>
    {% endif %}
    <div class="meta print-recipe" onclick="window.print()">
        <h3><i class="fa fa-print"></i> Print</h3>
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
                {% if direction.first %}
                    {% for item in direction %}
                        <li>{{ item[0]|liquify|markdownify }}</li>
                        <ol class="sub-direction">
                        {% for subdirection in item[1] %}
                            {% capture is_break %}{{ subdirection | slice: 0, 5 }}{% endcapture %}
                            {% if is_break == "break" %}
                                <li class="break">{{ subdirection|remove_first:"break: "|liquify|markdownify }}</li>
                            {% else %}
                                <li>{{ subdirection|liquify|markdownify }}</li>
                            {% endif %}
                        {% endfor %}
                        </ol>
                    {% endfor %}
                {% else %}
                    {% capture is_break %}{{ direction | slice: 0, 5 }}{% endcapture %}
                    {% if is_break == "break" %}
                        <li class="break">{{ direction| remove_first:"break: " |liquify|markdownify }}</li>
                    {% else %}
                        <li>{{ direction|liquify|markdownify }}</li>
                    {% endif %}
                {% endif %}
            {% endfor %}
        </ol>
    </div>
    {% if page.notes %}
    <div class="notes">
        <hr>
        <h2>Notes</h2>
        <ul>
            {% for note in page.notes %}
                <li><p>{{ note|liquify|markdownify }}</p></li>
            {% endfor %}
        </ul>       
    </div>
    {% endif %}
</div>
---
title: Browse Products
layout: browse
permalink: /browse/
metadata: products
filter_field: type
filter_value: Product
---
## Browse Products by Category

Explore all hardware products below. Use the search bar or click categories to filter items.

{% assign products = site.data.products %}

<div class="col-md-3">
  <div class="accordion mb-3" id="accordionBrowse">
    {% for product in products %}
      <div class="accordion-item">
        <{{ include.heading_level | default: 'h2' | strip }} class="accordion-header" id="heading{{ forloop.index }}">
          <button class="accordion-button{% unless include.open %} collapsed{% endunless %}" type="button" data-bs-toggle="collapse" data-bs-target="#collapse{{ forloop.index }}" aria-expanded="{% if include.open == true %}true{% else %}false{% endif %}" aria-controls="collapse{{ forloop.index }}">
              <a href="{{ product.url }}" style="text-decoration: none; color: inherit;">
                {{ product.subject | split: ';' | first }} 
              </a>
          </button>
        </{{ include.heading_level | default: 'h2' | strip }}>
        <div id="collapse{{ forloop.index }}" class="accordion-collapse collapse{% if include.open == true %} show{% endif %}" aria-labelledby="heading{{ forloop.index }}" data-bs-parent="#accordionBrowse">
          <div class="accordion-body">
            <a href="{{ product.url }}" class="btn btn-outline-dark btn-sm m-1">{{ product.title }}</a>  
          </div>
        </div>
      </div>
    {% endfor %}
  </div>
</div>

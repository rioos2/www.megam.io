---
# Page settings
layout: swagger
data: rioosv2
keywords:
comments: false

# Hero section
title: API Reference
description: Swagger Hub Rio OS v2 Open API specification and usage

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Quick Starters
        url: '/quick_starters'
    next:
        content: Home
        url: '/'
---

### v2


Refer [Rio OS - v2 in SwaggerHub: OpenAPI specification](https://app.swaggerhub.com/apis/riocorp/rioos/2.0){:target="_blank"}

<div class="callout callout--info">
    <p><strong>Caution</strong> API is subject to change until 2.0 is released.</p>    
</div>


{% for route in site.data.swagger.paths %}
<h1>0000</h1>h1>
<div class="swagger-paths">
    <h2 class="swagger-path">{{ route[0] }}</h>
    {% for method in route[1] %}
    <div class="swagger-method swagger-method-{{ method[0] }}">
        <h3 class="swagger-method-title">
            <a href="#" class="swagger-method-link">
                <span class="swagger-method-name">{{ method[0] | upcase }}</span>
                {{ method[1].summary }}
            </a>
        </h3>
        <div class="swagger-method-details">
            {% if method[1].parameters %}
            <div class="swagger-parameters">
                <h4>Parameters</h4>
                <table class="swagger-parameters-table">
                    <thead>
                        <tr>
                            <th>Name</th>
                            <th>Located in</th>
                            <th>Description</th>
                            <th>Type</th>
                        <tr>
                    </thead>
                    <tbody>
                        {% for parameter in method[1].parameters %}
                        <tr>
                            <td>
                                {% if parameter.required %}
                                <span class="swagger-parameter-required">
                                {% endif %}
                                {{ parameter.name }}
                                {% if parameter.required %}
                                </span>
                                {% endif %}
                            </td>
                            <td>{{ parameter.in }}</td>
                            <td>{{ parameter.description }}</td>
                            <td>
                                {% if parameter.type %}
                                {{ parameter.type | capitalize }}
                                {% if parameter.items %}
                                of {{ parameter.items.type | capitalize }}
                                {% endif %}
                                {% else %}
                                String
                                {% endif %}
                            </td>
                        </tr>
                        {% endfor %}
                    </tbody>
                </table>
            </div>
            {% endif %}
            {% if method[1].responses %}
            <div class="swagger-response">
                <h4>Responses</h4>
                {% for response in method[1].responses %}
                <h5>
                    <span class="swagger-response-code">{{ response[0] }}</span>
                    {{ response[1].description }}
                </h5>
                {% for content_type in swagger.produces %}
                    {% if response[1].examples[content_type] %}
                        {% assign example = response[1].examples[content_type] %}
                        {% if content_type contains 'json' %}
                            {% highlight json %}{{ example }}{% endhighlight %}
                        {% elsif content_type contains 'xml' %}
                            {% highlight xml %}{{ example }}{% endhighlight %}
                        {% else %}
                            {% highlight http %}{{ example }}{% endhighlight %}
                        {% endif %}
                    {% endif %}
                {% endfor %}
                {% endfor %}
            </div>
            {% endif %}
        </div>
    </div>
    {% endfor %}
</div>
{% endfor %}

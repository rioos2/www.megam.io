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
        url: '../../quick_starters'
    next:
        content: Home
        url: '/'
---

### v2


Refer [v2 OpenAPI specification](https://app.swaggerhub.com/apis/riocorp/rioos/2.0)

<div class="callout callout--info">
    <p><strong>Caution</strong> API is subject to change until 2.0 is released.</p>    
</div>



<script type="text/javascript">
// Helpers

var slice = Array.prototype.slice;

function $(expr, parent) {
    return typeof expr === "string" ? (parent || document).querySelector(expr) : expr || null;
}

function $$(expr, parent) {
    return slice.call((parent || document).querySelectorAll(expr));
}

$.bind = function(element, o) {
    alert("bind ="+ element);
    if (element) {
        for (var event in o) {
            var callback = o[event];

            event.split(/\s+/).forEach(function (event) {
                element.addEventListener(event, callback);
            });
        }
    }
};

$.toggleDetails = function (element) {

    alert(element.classList);
    if (element.classList.contains('open')) {
        element.classList.remove('open');
    }
    else {
        element.classList.add('open');
    }
}

// Initialization

function init() {
    console.log("init");
    $$('.swagger-method-title').forEach(function (title) {
        $.bind(title, {
            'click': function (e) {
                var details = $('.swagger-method-details', title.parentNode)
                alert("pn="+title.parentNode);
                $.toggleDetails(details);
                e.preventDefault();
            }
        });
    });
}


// DOM already loaded?
if (document.readyState !== "loading") {
    console.log("---- loading");
    init();
}
else {
    // Wait for it
    console.log("---- loading dom content");
    document.addEventListener("DOMContentLoaded", init);
}
</script>

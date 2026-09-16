# awaw.fyi.github.io
my website

# Installation
1. Install [Jekyll](https://jekyllrb.com/docs/installation/windows/) on Windows

# Build
- Use `jekyll build` to build a `_site` folder, where is live a static **site**

# Layouts
- Stored in `_layouts` folder
- `default.html` is default html file (wow!), its template for all pages on my site and that can be used by any page in my site and wrap around page content.
- `{{ content }}` is a special variable that returns the rendered content of the page on which it’s called.
# Liquid

- **Use Liquid features [here](https://jekyllrb.com/docs/step-by-step/02-liquid/)**
##### Tags
Tags define the logic and control flow for templates. Use curly braces and percent signs for tags: `{%` and `%}`.

For example:
```
{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
```

##### Filters

Filters change the output of a Liquid object. They are used within an output and are separated by a `|`.

For example:
```
{{ "hi" | capitalize }}
```

This displays `Hi` instead of `hi`.
[Learn more about the filters](https://jekyllrb.com/docs/liquid/filters/) available.

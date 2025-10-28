---
layout: default
---

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

This is a test.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# My Experience with AG-Grid & SlickGrid

I’ve worked extensively with **AG-Grid** and **SlickGrid**, two of the most powerful JavaScript data-grid libraries used for building real-time, interactive data tables.
My focus has been on integrating these grids into **high-performance dashboards**, **trading tools**, and **analytics systems** that demand precision, speed, and dynamic visual updates.

## AG-Grid

AG-Grid has been my preferred solution for building enterprise-level data tables due to its comprehensive API, responsive design, and real-time update capabilities.

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Key Work:

* Implemented live price and delta updates using MutationObservers and WebSocket feeds.

* Built custom cell renderers to display ↑ / ↓ indicators and conditional color coding.

* Integrated AG-Grid with Blazor and TypeScript, enabling reactive updates across front-end and back-end.

* Tuned performance for large datasets by adjusting change detection, row virtualization, and event throttling.

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

## SlickGrid

SlickGrid is lightweight, fast, and ideal for scenarios requiring direct DOM control and minimal framework overhead.
I’ve used it to create highly responsive tables for internal tools and performance-critical apps.

### Key Work:

1.  Customized cell formatters to render delta percentages and real-time price indicators.
2.  Used direct DOM observers to track visual changes for debugging and analytics.
3.  Enhanced rendering speed for large static datasets
4.  

### AG-Grid vs SlickGrid — My Insights

| Feature       | AG-Grid                           | SlickGrid                       |
|:--------------|:----------------------------------|:--------------------------------|
| Performance   | Excellent with large dynamic data | Exceptional for static data     |
| Customization | API-driven and component-based    | DOM-level flexibility           |
| Integration   | Works with React, Angular, Blazor | Primarily `vanilla` JS / jQuery |
| Ecosystem     | Active, enterprise support        | Legacy, open-source community   |
| Best For      | Real-time dashboards & analytics  | Lightweight, fast-loading UIs   |

### There's a horizontal rule below this.

* * *

### Lessons Learned

Working deeply with both grids taught me to:

*   Optimize DOM updates for real-time performance.
*   Balance framework abstraction vs raw control.
*   Build responsive UIs that can handle frequent data mutations gracefully.
*   Design data visualizations that stay intuitive under heavy load.

### Summary

Both AG-Grid and SlickGrid have unique strengths — mastering them has helped me design systems that combine speed, clarity, and scalability in real-time data applications.

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```

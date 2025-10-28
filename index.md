---
layout: default
---

Text can be _italic_, or ~~strikethrough~~.

[Link to another page](./blazor-datafeeds.html).

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
(function () {
  const lastPrices = {};

  function checkAgGrid() {
    const tickerCells = document.querySelectorAll('b.custom-ticker');
    tickerCells.forEach(tickerEl => {
      const ticker = tickerEl.textContent.trim();
      if (ticker !== 'BTCUSDT') return;

      const row = tickerEl.closest('[role="row"]');
      if (!row) return;

      const priceCell = row.querySelector('[col-id="price"]');
      const deltaEl = priceCell?.querySelector('[data-ref="eDelta"]');
      const valueEl = priceCell?.querySelector('[data-ref="eValue"]');
      if (!priceCell || !valueEl) return;

      const price = parseFloat(valueEl.textContent.replace(/,/g, ''));
      const deltaText = deltaEl?.textContent.trim() || '';
      const deltaSign = deltaText.includes('↓') ? -1 : 1;
      const deltaVal = parseFloat(deltaText.replace(/[↑↓%\s]/g, '')) * deltaSign;

      const lastPrice = lastPrices[ticker];
      if (lastPrice !== undefined) {
        const expected = ((price - lastPrice) / lastPrice) * 100;
        if (Math.abs(deltaVal - expected) > 0.01) {
          console.warn(`⚠️ [AG-GRID] MISMATCH — ${ticker}: Delta ${deltaVal.toFixed(4)}% vs Expected ${expected.toFixed(4)}% (Price: ${price}, Last: ${lastPrice})`);
        }
      }

      lastPrices[ticker] = price;
    });
  }

  const grid = document.querySelector('.ag-root') || document.body;
  if (grid) {
    const observer = new MutationObserver(checkAgGrid);
    observer.observe(grid, { childList: true, subtree: true });
    console.log('✅ [AG-GRID] watcher active for BTCUSDT');
  } else {
    console.warn('⚠️ [AG-GRID] not found.');
  }
})();

(function () {
  const lastPriceMap = {};

  function checkSlickGrid() {
    const rows = document.querySelectorAll('.slick-row');
    rows.forEach(row => {
      const tickerCell = row.querySelector('.slick-cell:nth-child(1)');
      if (!tickerCell) return;

      const ticker = tickerCell.textContent.trim();
      if (ticker !== 'BTCUSDT') return;

      const priceCell = row.querySelector('.slick-cell:nth-child(3)');
      if (!priceCell) return;

      const spans = priceCell.querySelectorAll('span');
      let price = 0, deltaPct = 0, deltaSign = 1;
      spans.forEach(span => {
        const text = span.textContent.trim();
        if (/^[0-9,.]+$/.test(text)) {
          price = parseFloat(text.replace(/,/g, ''));
        }
        if (text.includes('%')) {
          deltaSign = text.includes('↓') ? -1 : 1;
          deltaPct = parseFloat(text.replace(/[↑↓%\s]/g, '')) * deltaSign;
        }
      });

      if (!price) return;

      const lastPrice = lastPriceMap[ticker];
      if (lastPrice !== undefined) {
        const expectedPct = ((price - lastPrice) / lastPrice) * 100;
        if (Math.abs(deltaPct - expectedPct) > 0.01) {
          console.warn(`⚠️ [SLICKGRID] MISMATCH — ${ticker}: Delta ${deltaPct.toFixed(4)}% vs Expected ${expectedPct.toFixed(4)}% (Price: ${price}, Last: ${lastPrice})`);
        }
      }

      lastPriceMap[ticker] = price;
    });
  }

  const grid = document.querySelector('.slick-viewport') || document.body;
  if (grid) {
    const observer = new MutationObserver(checkSlickGrid);
    observer.observe(grid, { childList: true, subtree: true });
    console.log('✅ [SLICKGRID] watcher active for BTCUSDT');
  } else {
    console.warn('⚠️ [SLICKGRID] not found.');
  }
})();
```

## SlickGrid

SlickGrid is lightweight, fast, and ideal for scenarios requiring direct DOM control and minimal framework overhead.
I’ve used it to create highly responsive tables for internal tools and performance-critical apps.

### Key Work:

1.  Customized cell formatters to render delta percentages and real-time price indicators.
2.  Used direct DOM observers to track visual changes for debugging and analytics.
3.  Enhanced rendering speed for large static datasets
4.  Integrated with modern TypeScript modules despite its legacy jQuery roots.

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

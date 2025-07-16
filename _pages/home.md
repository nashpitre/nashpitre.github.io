---
layout: home
permalink: /index.html
---

![Now](assets/now.jpg)

Dad to a little girl that loves reading books and playing Animal Crossing. Preparing for twin boys in the fall. Doing tech support for our local hospital. Running, lifting, and playing basketball daily. Creating stories in silence. 

*—May 6th, 2025*

<style>
  #news-ticker {
    background: #479db1;
    color: #ffffff;
    overflow: hidden;
    white-space: nowrap;
    font-weight: bold;
    font-size: 16px;
    padding: 10px 16px;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    border-radius: 6px;
    box-sizing: border-box;
  }

  #news-ticker a {
    color: #ffffff;
    margin-right: 40px;
    text-decoration: none;
    display: inline-block;
  }

  #news-ticker a:hover {
    text-decoration: underline;
  }

  .ticker-content {
    display: inline-block;
    white-space: nowrap;
    animation: ticker-scroll 60s linear infinite;
  }

  @keyframes ticker-scroll {
    from {
      transform: translateX(100%);
    }
    to {
      transform: translateX(-100%);
    }
  }
</style>

<div id="news-ticker">
  <div class="ticker-content">
    Loading latest stories...
  </div>
</div>

<script>
  const tickerContent = document.querySelector(".ticker-content");

  fetch("/assets/reeder.json")
    .then(res => res.json())
    .then(data => {
      const items = (data.items || []).slice(0, 5);
      if (items.length === 0) {
        tickerContent.textContent = "No news available.";
        return;
      }

      tickerContent.innerHTML = items.map(item => {
        const title = item.title || "Untitled";
        const url = item.url || "#";
        return `<a href="${url}" target="_blank" rel="noopener noreferrer">${title}</a>`;
      }).join("");
    })
    .catch(error => {
      tickerContent.textContent = "Could not load news.";
      console.error("Ticker error:", error);
    });
</script>

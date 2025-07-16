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
    color: #ddd;
    overflow: hidden;
    white-space: nowrap;
    font-weight: bold;
    font-size: 16px;
    padding: 8px 16px;
    font-family: Arial, sans-serif;
    border-radius: 4px;
  }

  #news-ticker a {
    color: #ddd;
    margin-right: 50px;
    text-decoration: none;
    display: inline-block;
  }

  #news-ticker a:hover {
    text-decoration: underline;
  }

  .ticker-content {
    display: inline-block;
    white-space: nowrap;
    animation: ticker-scroll 90s linear infinite;
  }

  @keyframes ticker-scroll {
    0% {
      transform: translateX(100%);
    }
    100% {
      transform: translateX(-100%);
    }
  }
</style>

<div id="news-ticker">
  <div class="ticker-content">Loading news…</div>
</div>

<script>
  const tickerContent = document.querySelector("#news-ticker .ticker-content");
  tickerContent.style.animationPlayState = 'running';

  fetch("/assets/reeder.json")
    .then(res => res.json())
    .then(data => {
      const items = (data.items || []).slice(0, 5);
      if (!items.length) {
        tickerContent.textContent = "No news items found.";
        return;
      }
      let html = "";
      items.forEach(item => {
        html += `<a href="${item.url || '#'}" target="_blank" rel="noopener noreferrer">${item.title || 'Untitled'}</a>`;
      });
      tickerContent.innerHTML = html;
    })
    .catch(err => {
      tickerContent.textContent = `Could not load news: ${err.message}`;
      console.error(err);
    });
</script>

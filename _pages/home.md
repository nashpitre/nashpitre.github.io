---
layout: home
permalink: /index.html
---

![Now](assets/now.jpg)

Dad to a little girl that loves reading books and playing Animal Crossing. Preparing for twin boys in the fall. Doing tech support for our local hospital. Running, lifting, and playing basketball daily. Creating stories in silence. 

*—May 6th, 2025*

<style>
  #news-ticker {
    background: #111;
    color: #ddd;
    overflow: hidden;
    white-space: nowrap;
    font-weight: bold;
    font-size: 16px;
    padding: 8px 16px;
    font-family: Arial, sans-serif;
    border-radius: 4px;
    position: relative;
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
    padding-left: 100%;
    animation: ticker-scroll linear infinite;
    white-space: nowrap;
    will-change: transform;
    position: relative;
    color: inherit;
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
  fetch("/assets/reeder.json")
    .then(res => res.json())
    .then(data => {
      const tickerContent = document.querySelector("#news-ticker .ticker-content");
      const items = (data.items || []).slice(0, 5);

      let html = "";
      items.forEach(item => {
        html += `<a href="${item.url || '#'}" target="_blank" rel="noopener noreferrer">${item.title || 'Untitled'}</a>`;
      });

      tickerContent.innerHTML = html;

      // Duplicate for seamless loop
      const clone = tickerContent.cloneNode(true);
      tickerContent.parentNode.appendChild(clone);

      // Adjust animation duration for smooth scroll speed
      const container = document.getElementById("news-ticker");
      const contentWidth = tickerContent.offsetWidth;
      const containerWidth = container.offsetWidth;
      const duration = (contentWidth + containerWidth) / 100; // px per second speed (adjust 100 to tweak speed)
      tickerContent.style.animationDuration = duration + "s";
      clone.style.animationDuration = duration + "s";
    })
    .catch(err => {
      document.querySelector("#news-ticker .ticker-content").textContent =
        `Could not load news: ${err.message}`;
      console.error(err);
    });
</script>

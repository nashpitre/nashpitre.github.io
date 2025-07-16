---
layout: home
permalink: /index.html
---

![Now](assets/now.jpg)

Dad to a little girl that loves reading books and playing Animal Crossing. Preparing for twin boys in the fall. Doing tech support for our local hospital. Running, lifting, and playing basketball daily. Creating stories in silence. 

*—May 6th, 2025*

----

<style>
  #news-ticker {
    overflow: hidden;
    white-space: nowrap;
    box-sizing: border-box;
    background: #111; /* dark background like ESPN ticker */
    color: #eee;
    padding: 8px 16px;
    font-family: Arial, sans-serif;
    font-weight: bold;
    font-size: 16px;
    border-radius: 4px;
  }

  #news-ticker a {
    color: #f00; /* ESPN red accent */
    text-decoration: none;
    margin-right: 50px;
    display: inline-block;
  }

  #news-ticker a:hover {
    text-decoration: underline;
  }

  /* Animation keyframes */
  @keyframes ticker-scroll {
    0% {
      transform: translateX(100%);
    }
    100% {
      transform: translateX(-100%);
    }
  }

  #news-ticker .ticker-content {
    display: inline-block;
    padding-left: 100%;
    animation: ticker-scroll linear infinite;
    animation-duration: 30s; /* adjust speed here */
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
    tickerContent.innerHTML = "";

    const items = (data.items || []).slice(0, 10);

    items.forEach(item => {
      const a = document.createElement("a");
      a.href = item.url || "#";
      a.textContent = item.title || "Untitled";
      a.target = "_blank";
      a.rel = "noopener noreferrer";
      tickerContent.appendChild(a);
    });

    // Duplicate the items to create a seamless loop effect
    const clone = tickerContent.cloneNode(true);
    tickerContent.parentNode.appendChild(clone);

    // Calculate animation duration based on text width (optional, for smoother speed)
    const container = document.getElementById("news-ticker");
    const contentWidth = tickerContent.offsetWidth;
    const containerWidth = container.offsetWidth;
    const duration = (contentWidth + containerWidth) / 100; // 100px per second speed
    tickerContent.style.animationDuration = duration + "s";
    clone.style.animationDuration = duration + "s";
  })
  .catch(err => {
    const tickerContent = document.querySelector("#news-ticker .ticker-content");
    tickerContent.textContent = `Could not load news: ${err.message}`;
    console.error(err);
  });
</script>

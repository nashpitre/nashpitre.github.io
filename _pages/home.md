---
layout: home
permalink: /index.html
---

![Now](assets/now.jpg)

Dad to a little girl that loves reading books and playing Animal Crossing. Preparing for twin boys in the fall. Doing tech support for our local hospital. Running, lifting, and playing basketball daily. Creating stories in silence. 

*—May 6th, 2025*

<br>

<style>
  #news-container {
    display: flex;
    justify-content: center;
    padding: 20px 0;
  }

  #news-paragraph {
    border: 1px solid #ccc;
    padding: 12px 16px;
    border-radius: 6px;
    background: none;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    line-height: 1.6;
    color: #333;
    font-variant: small-caps;
    transition: color 0.3s ease, border-color 0.3s ease;
    max-width: 600px;
    text-align: center;
  }

  #news-paragraph a {
    color: inherit;
    text-decoration: none;
    font-weight: normal;
  }

  #news-paragraph a:hover {
    text-decoration: none;
  }

  @media (prefers-color-scheme: dark) {
    #news-paragraph {
      color: #fff !important;
      border-color: #555;
    }
  }
</style>

<div id="news-container">
  <p id="news-paragraph">Loading…</p>
</div>

<script>
fetch("https://reederapp.net/Tkkabi0mQNe7RQtZCseHJg")
  .then(res => res.json())
  .then(data => {
    const paragraph = document.getElementById("news-paragraph");
    const items = (data.items || []).slice(0, 5);

    if (items.length === 0) {
      paragraph.textContent = "No news available.";
      return;
    }

    const links = items.map(item => {
      const title = item.title || "Untitled";
      const url = item.url || "#";
      return `<a href="${url}" target="_blank" rel="noopener noreferrer">${title}</a>`;
    });

    let sentence = "";

    if (links.length === 1) {
      sentence = links[0];
    } else if (links.length === 2) {
      sentence = `${links[0]} and ${links[1]}`;
    } else {
      sentence = `${links.slice(0, -1).join(", ")}, and ${links[links.length - 1]}`;
    }

    paragraph.innerHTML = `Today’s news: ${sentence}.`;
  })
  .catch(err => {
    document.getElementById("news-paragraph").textContent =
      `Could not load news: ${err.message}`;
    console.error(err);
  });
</script>
<br>

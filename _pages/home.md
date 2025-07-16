---
layout: home
permalink: /index.html
---

![Now](assets/now.jpg)

Dad to a little girl that loves reading books and playing Animal Crossing. Preparing for twin boys in the fall. Doing tech support for our local hospital. Running, lifting, and playing basketball daily. Creating stories in silence. 

*—May 6th, 2025*

----

<style>
  #news-paragraph a {
    color: inherit;
    text-decoration: none;
    font-weight: normal;
  }

  #news-paragraph a:hover {
    text-decoration: none;
  }
</style>

<p id="news-paragraph">Loading…</p>

<script>
function sentenceCase(text) {
  if (!text) return "";
  text = text.trim();
  return text.charAt(0).toUpperCase() + text.slice(1).toLowerCase();
}

fetch("/assets/reeder.json")
  .then(res => res.json())
  .then(data => {
    const paragraph = document.getElementById("news-paragraph");
    const items = (data.items || []).slice(0, 5);

    if (items.length === 0) {
      paragraph.textContent = "No news available.";
      return;
    }

    const links = items.map(item => {
      const title = sentenceCase(item.title || "Untitled");
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

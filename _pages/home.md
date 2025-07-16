---
layout: home
permalink: /index.html
---

![Now](assets/now.jpg)

Dad to a little girl that loves reading books and playing Animal Crossing. Preparing for twin boys in the fall. Doing tech support for our local hospital. Running, lifting, and playing basketball daily. Creating stories in silence. 

*—May 6th, 2025*

----

<h2>Today’s News</h2>
<ul id="news-list">Loading...</ul>

<script>
fetch("https://reederapp.net/Tkkabi0mQNe7RQtZCseHJg.json")
  .then(res => res.json())
  .then(data => {
    const list = document.getElementById("news-list");
    list.innerHTML = ""; // Clear "Loading..."

    const items = (data.items || []).slice(0, 10);

    if (!items.length) {
      list.innerHTML = "<li>No items found.</li>";
      return;
    }

    items.forEach(item => {
      const li = document.createElement("li");
      const a = document.createElement("a");

      a.href = item.url || "#";
      a.textContent = item.title || "Untitled";
      a.target = "_blank";
      a.rel = "noopener noreferrer";

      li.appendChild(a);
      list.appendChild(li);
    });
  })
  .catch(err => {
    const list = document.getElementById("news-list");
    list.innerHTML = `<li>Failed to load news: ${err.message}</li>`;
    console.error("Error fetching news:", err);
  });
</script>

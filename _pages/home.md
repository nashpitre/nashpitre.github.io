---
layout: home
permalink: /index.html
---

![Now](assets/now.jpg)

Dad to a little girl that loves reading books and playing Animal Crossing. Preparing for twin boys in the fall. Doing tech support for our local hospital. Running, lifting, and playing basketball daily. Creating stories in silence. 

*—May 6th, 2025*

----

<h2>Today’s News</h2>
<ul id="news-list"></ul>

<script>
fetch("https://reederapp.net/Tkkabi0mQNe7RQtZCseHJg.json")
  .then(res => res.json())
  .then(data => {
    const list = document.getElementById("news-list");
    const items = (data.items || data.entries || []).slice(0, 10);

    items.forEach(item => {
      const li = document.createElement("li");
      const a = document.createElement("a");
      a.href = item.url || item.link || "#";
      a.textContent = item.title;
      a.target = "_blank";
      a.rel = "noopener noreferrer";
      li.appendChild(a);
      list.appendChild(li);
    });
  });
</script>

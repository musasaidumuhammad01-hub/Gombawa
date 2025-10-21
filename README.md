# Gombawa
class=""
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Search Filter with Categories</title>
  <style>
    body { font-family: Arial; padding: 20px; }
    input, select {
      padding: 10px;
      margin: 10px 0;
      width: 300px;
    }
    ul { list-style: none; padding: 0; }
    li { padding: 5px 0; }
  </style>
</head>
<body>

  <h2>Search Filter with Categories</h2>

  <input type="text" id="searchInput" placeholder="Search item...">
  <select id="categorySelect">
    <option value="all">All Categories</option>
    <option value="fruits">Fruits</option>
    <option value="vegetables">Vegetables</option>
    <option value="drinks">Drinks</option>
  </select>

  <ul id="itemList">
    <li data-category="fruits">Apple</li>
    <li data-category="fruits">Banana</li>
    <li data-category="vegetables">Carrot</li>
    <li data-category="vegetables">Lettuce</li>
    <li data-category="drinks">Milk</li>
    <li data-category="drinks">Juice</li>
  </ul>

  <script>
    const searchInput = document.getElementById("searchInput");
    const categorySelect = document.getElementById("categorySelect");
    const items = document.querySelectorAll("#itemList li");
 function filterItems() {
      const searchText = searchInput.value.toLowerCase();
      const selectedCategory = categorySelect.value;

      items.forEach(item => {
        const itemText = item.textContent.toLowerCase();
        const itemCategory = item.getAttribute("data-category");

        const matchesText = itemText.includes(searchText);
        const matchesCategory = selectedCategory === "all" || itemCategory === selectedCategory;

        item.style.display = (matchesText && matchesCategory) ? "" : "none";
      });
    }

    searchInput.addEventListener("input", filterItems);
    categorySelect.addEventListener("change", filterItems);
  </script>

</body>
</html>


<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#101014">
  <title>My-world | دنیای فیلم و سریال</title>
  <style>
    :root {
      color-scheme: dark;
      --bg: #101014;
      --panel: #1a1a22;
      --text: #f6f6fa;
      --muted: #a6a6b4;
      --accent: #a78bfa;
    }

    * { box-sizing: border-box; }

    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      font-family: Tahoma, Arial, sans-serif;
    }

    header {
      padding: 32px 18px 24px;
      text-align: center;
      background: linear-gradient(135deg, #28203c, #111116);
      border-bottom: 1px solid #302b3d;
    }

    header h1 {
      margin: 0 0 10px;
      font-size: clamp(28px, 6vw, 42px);
      color: var(--accent);
    }

    header p { color: var(--muted); margin-bottom: 0; }

    main {
      max-width: 1250px;
      margin: auto;
      padding: 22px 14px;
    }

    .controls {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
      margin-bottom: 20px;
    }

    input, select {
      width: 100%;
      min-width: 0;
      padding: 13px;
      border-radius: 12px;
      border: 1px solid #393943;
      background: var(--panel);
      color: var(--text);
      font-size: 14px;
    }

    input { grid-column: 1 / -1; }

    .tabs {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-bottom: 16px;
    }

    button {
      cursor: pointer;
      border: 1px solid #393943;
      border-radius: 10px;
      background: var(--panel);
      color: var(--text);
      padding: 10px 15px;
      font-size: 14px;
    }

    button.active {
      background: var(--accent);
      color: #17121f;
      border-color: var(--accent);
      font-weight: bold;
    }

    #status {
      color: var(--muted);
      margin: 12px 0 18px;
      font-size: 14px;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(5, minmax(0, 1fr));
      gap: 16px;
    }

    .card {
      overflow: hidden;
      border: 1px solid #2d2d38;
      border-radius: 13px;
      background: var(--panel);
      min-width: 0;
      transition: transform .2s, border-color .2s;
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: var(--accent);
    }

    .poster {
      display: block;
      width: 100%;
      aspect-ratio: 2 / 3;
      object-fit: cover;
      background: #292934;
    }

    .info { padding: 11px; }

    .info h2 {
      font-size: 14px;
      line-height: 1.7;
      margin: 0 0 7px;
      overflow-wrap: anywhere;
    }

    .meta {
      color: var(--muted);
      font-size: 12px;
      line-height: 1.9;
    }

    .rating {
      color: #f5ca73;
      font-weight: bold;
    }

    footer {
      text-align: center;
      color: var(--muted);
      padding: 28px 12px;
      font-size: 12px;
    }

    @media (max-width: 900px) {
      .grid { grid-template-columns: repeat(4, minmax(0, 1fr)); }
    }

    @media (max-width: 600px) {
      .grid { grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 12px; }
      main { padding: 16px 10px; }
      header { padding: 26px 12px; }
    }
  </style>
</head>
<body>
  <header>
    <h1>My-world 🎬</h1>
    <p>دنیای فیلم‌ها و سریال‌های ماندگار</p>
  </header>

  <main>
    <div class="controls">
      <input id="search" type="search"
        placeholder="جست‌وجوی نام فیلم یا سریال...">

      <select id="genre">
        <option value="">همه ژانرها</option>
      </select>

      <select id="sort">
        <option value="rating">مرتب‌سازی بر اساس امتیاز</option>
        <option value="year">جدیدترین سال انتشار</option>
        <option value="title">نام انگلیسی</option>
      </select>
    </div>

    <div class="tabs">
      <button class="active" data-type="all">همه</button>
      <button data-type="movie">فیلم‌ها</button>
      <button data-type="tv">سریال‌ها</button>
    </div>

    <p id="status">در حال دریافت اطلاعات فیلم‌ها و سریال‌ها...</p>
    <section id="grid" class="grid"></section>
  </main>

  <footer>
    اطلاعات و تصاویر از TMDB دریافت می‌شوند.
    این سایت وابسته یا مورد تأیید TMDB نیست.
  </footer>

  <script>
    // کلید API خودت را اینجا وارد کن
    const API_KEY = "YOUR_TMDB_API_KEY";
    const API = "https://api.themoviedb.org/3";
    const IMG = "https://image.tmdb.org/t/p/w500";

    const grid = document.getElementById("grid");
    const status = document.getElementById("status");
    const search = document.getElementById("search");
    const genreSelect = document.getElementById("genre");
    const sortSelect = document.getElementById("sort");

    let movies = [];
    let selectedType = "all";
    let genres = { movie: {}, tv: {} };

    async function request(path) {
      const separator = path.includes("?") ? "&" : "?";
      const url = API + path + separator +
        "api_key=" + encodeURIComponent(API_KEY) +
        "&language=en-US";

      const response = await fetch(url);

      if (!response.ok) {
        throw new Error("خطای API: " + response.status);
      }

      return response.json();
    }

    async function loadGenres(type) {
      const data = await request("/genre/" + type + "/list");
      for (const item of data.genres) {
        genres[type][item.id] = item.name;
      }
    }

    async function loadTop(type) {
      // هر صفحه معمولاً ۲۰ عنوان دارد؛ ۱۳ صفحه برای ۲۵۰ عنوان
      const pages = Array.from({ length: 13 }, (_, i) => i + 1);

      const results = await Promise.all(
        pages.map(page =>
          request("/" + type + "/top_rated?page=" + page)
        )
      );

      return results
        .flatMap(data => data.results)
        .slice(0, 250)
        .map(item => ({
          ...item,
          media_type: type,
          displayTitle: type === "movie"
            ? item.title
            : item.name,
          displayDate: type === "movie"
            ? item.release_date
            : item.first_air_date
        }));
    }

    function getYear(item) {
      return item.displayDate
        ? item.displayDate.slice(0, 4)
        : "نامشخص";
    }

    function getGenreNames(item) {
      const dictionary = genres[item.media_type];
      return (item.genre_ids || [])
        .map(id => dictionary[id])
        .filter(Boolean);
    }

    function populateGenres() {
      const names = new Set();

      for (const item of movies) {
        getGenreNames(item).forEach(name => names.add(name));
      }

      genreSelect.innerHTML =
        '<option value="">همه ژانرها</option>';

      [...names].sort().forEach(name => {
        const option = document.createElement("option");
        option.value = name;
        option.textContent = name;
        genreSelect.appendChild(option);
      });
    }

    function makeCard(item) {
      const card = document.createElement("article");
      card.className = "card";

      const img = document.createElement("img");
      img.className = "poster";
      img.loading = "lazy";
      img.alt = "پوستر " + item.displayTitle;
      img.src = item.poster_path
        ? IMG + item.poster_path
        : "https://placehold.co/400x600/292934/ffffff?text=No+Poster";

      const info = document.createElement("div");
      info.className = "info";

      const title = document.createElement("h2");
      title.textContent = item.displayTitle || "بدون عنوان";

      const meta = document.createElement("div");
      meta.className = "meta";

      const typeName = item.media_type === "movie"
        ? "فیلم"
        : "سریال";

      const rating = Number(item.vote_average || 0).toFixed(1);
      const genreNames = getGenreNames(item).slice(0, 2).join("، ");

      meta.textContent =
        typeName + " · " + getYear(item) +
        (genreNames ? " · " + genreNames : "");

      const score = document.createElement("div");
      score.className = "rating";
      score.textContent = "★ " + rating + " / 10";

      info.append(title, meta, score);
      card.append(img, info);

      return card;
    }

    function render() {
      const query = search.value.trim().toLowerCase();
      const selectedGenre = genreSelect.value;
      const sort = sortSelect.value;

      let list = movies.filter(item => {
        const matchesType =
          selectedType === "all" ||
          item.media_type === selectedType;

        const title = (item.displayTitle || "").toLowerCase();
        const matchesSearch = title.includes(query);
        const matchesGenre = !selectedGenre ||
          getGenreNames(item).includes(selectedGenre);

        return matchesType && matchesSearch && matchesGenre;
      });

      if (sort === "rating") {
        list.sort((a, b) => b.vote_average - a.vote_average);
      } else if (sort === "year") {
        list.sort((a, b) =>
          (b.displayDate || "").localeCompare(a.displayDate || "")
        );
      } else {
        list.sort((a, b) =>
          (a.displayTitle || "").localeCompare(b.displayTitle || "")
        );
      }

      grid.replaceChildren();

      const fragment = document.createDocumentFragment();
      list.forEach(item => fragment.appendChild(makeCard(item)));
      grid.appendChild(fragment);

      status.textContent =
        list.length + " عنوان از " + movies.length + " عنوان";
    }

    document.querySelectorAll("[data-type]").forEach(button => {
      button.addEventListener("click", () => {
        selectedType = button.dataset.type;

        document.querySelectorAll("[data-type]").forEach(btn => {
          btn.classList.toggle("active", btn === button);
        });

        render();
      });
    });

    search.addEventListener("input", render);
    genreSelect.addEventListener("change", render);
    sortSelect.addEventListener("change", render);

    async function init() {
      if (!API_KEY || API_KEY === "YOUR_TMDB_API_KEY") {
        status.textContent =
          "ابتدا کلید API سرویس TMDB را در کد وارد کن.";
        return;
      }

      try {
        status.textContent = "در حال بارگذاری فیلم‌ها و سریال‌ها...";

        await Promise.all([
          loadGenres("movie"),
          loadGenres("tv")
        ]);

        const [movieList, tvList] = await Promise.all([
          loadTop("movie"),
          loadTop("tv")
        ]);

        movies = [...movieList, ...tvList];
        populateGenres();
        render();
      } catch (error) {
        console.error(error);
        status.textContent =
          "دریافت اطلاعات ناموفق بود. کلید API و اتصال اینترنت را بررسی کن.";
      }
    }

    init();
  </script>
</body>
</html>
# My-world

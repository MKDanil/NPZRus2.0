``html
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Вместе восстановим НПЗ</title>
  <style>
    /* ===== ОБЩИЕ СТИЛИ ===== */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
      background: #f4f6fa;
      color: #1a1f2e;
      line-height: 1.5;
    }
    a { text-decoration: none; color: inherit; }
    .container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
    button { cursor: pointer; }

    /* ===== ШАПКА ===== */
    .header {
      background: #0b1424;
      color: #fff;
      padding: 16px 0;
      position: sticky;
      top: 0;
      z-index: 100;
      box-shadow: 0 4px 20px rgba(0,0,0,0.3);
    }
    .header .container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
    }
    .logo {
      font-size: 24px;
      font-weight: 700;
      letter-spacing: 1px;
    }
    .logo span { color: #e85a2c; }
    .nav {
      display: flex;
      gap: 24px;
      flex-wrap: wrap;
    }
    .nav a {
      font-size: 16px;
      padding: 6px 0;
      border-bottom: 2px solid transparent;
      transition: 0.2s;
    }
    .nav a:hover, .nav a.active {
      border-bottom-color: #e85a2c;
      color: #e85a2c;
    }
    .btn-donate {
      background: #e85a2c;
      padding: 8px 22px;
      border-radius: 30px;
      font-weight: 600;
      color: #fff !important;
      border: none;
      transition: 0.3s;
    }
    .btn-donate:hover {
      background: #c94b1f;
      transform: scale(1.03);
    }
    .burger {
      display: none;
      font-size: 28px;
      background: none;
      border: none;
      color: #fff;
    }

    /* ===== СТРАНИЦЫ (вкладки) ===== */
    .page {
      display: none;
      padding: 40px 0 60px;
      animation: fade 0.4s ease;
    }
    .page.active { display: block; }
    @keyframes fade { from { opacity: 0.2; } to { opacity: 1; } }

    h1 {
      font-size: 40px;
      margin-bottom: 20px;
      line-height: 1.2;
    }
    h2 {
      font-size: 30px;
      margin: 30px 0 16px;
    }
    h3 { font-size: 22px; margin: 20px 0 10px; }
    p { margin-bottom: 16px; font-size: 18px; }

    /* ===== ГЛАВНАЯ ===== */
    .hero {
      background: linear-gradient(135deg, #0b1424 0%, #1a2a4a 100%);
      color: #fff;
      padding: 60px 20px;
      border-radius: 20px;
      text-align: center;
      margin-bottom: 40px;
    }
    .hero h1 { font-size: 48px; }
    .hero p { font-size: 20px; max-width: 700px; margin: 16px auto; }
    .hero-buttons { display: flex; gap: 20px; justify-content: center; flex-wrap: wrap; margin: 20px 0; }
    .btn-primary, .btn-secondary {
      padding: 14px 40px;
      border-radius: 50px;
      font-weight: 700;
      font-size: 18px;
      border: none;
      transition: 0.3s;
    }
    .btn-primary { background: #e85a2c; color: #fff; }
    .btn-primary:hover { background: #c94b1f; transform: translateY(-2px); }
    .btn-secondary { background: #2a5f8a; color: #fff; }
    .btn-secondary:hover { background: #1e4a6b; transform: translateY(-2px); }
    .ticker {
      background: #1e2f4a;
      padding: 12px;
      border-radius: 12px;
      font-size: 18px;
      margin-top: 20px;
    }

    /* ===== СЧЁТЧИКИ ===== */
    .stats {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 20px;
      margin: 30px 0;
    }
    .stat-card {
      background: #fff;
      padding: 24px;
      border-radius: 16px;
      text-align: center;
      box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    }
    .stat-card .number {
      font-size: 36px;
      font-weight: 800;
      color: #0b1424;
    }
    .stat-card .label { font-size: 16px; color: #555; }

    .grid-3 {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 30px;
      margin: 30px 0;
    }
    .card {
      background: #fff;
11:37


padding: 24px;
      border-radius: 16px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    }
    .card img { width: 100%; border-radius: 12px; margin-bottom: 12px; }

    /* ===== НОВОСТИ ===== */
    .news-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 20px; }
    .news-item { background: #fff; border-radius: 16px; overflow: hidden; box-shadow: 0 4px 12px rgba(0,0,0,0.05); }
    .news-item img { width: 100%; height: 180px; object-fit: cover; }
    .news-item .text { padding: 16px; }
    .news-item .date { color: #888; font-size: 14px; }
    .news-item h4 { margin: 8px 0; }

    /* ===== ВКЛАДКИ ПОМОЩИ ===== */
    .tabs { display: flex; gap: 12px; flex-wrap: wrap; margin-bottom: 30px; }
    .tab-btn {
      padding: 12px 28px;
      background: #e0e6f0;
      border: none;
      border-radius: 30px;
      font-weight: 600;
      transition: 0.3s;
    }
    .tab-btn.active { background: #0b1424; color: #fff; }
    .tab-content { display: none; }
    .tab-content.active { display: block; }
    .form-group { margin: 16px 0; }
    .form-group label { display: block; font-weight: 600; margin-bottom: 6px; }
    .form-group input, .form-group select, .form-group textarea {
      width: 100%;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 16px;
    }
    .form-group textarea { height: 100px; }

    /* ===== ТАЙМЛАЙН ===== */
    .timeline { position: relative; padding-left: 30px; border-left: 3px solid #e85a2c; }
    .timeline-item { margin-bottom: 30px; }
    .timeline-item .date { font-weight: 700; color: #e85a2c; }
    .timeline-item p { margin: 6px 0; }

    /* ===== FAQ ===== */
    .faq-item { border-bottom: 1px solid #ddd; padding: 16px 0; }
    .faq-question { font-weight: 700; cursor: pointer; display: flex; justify-content: space-between; }
    .faq-question::after { content: '+'; font-size: 24px; }
    .faq-item.open .faq-question::after { content: '−'; }
    .faq-answer { display: none; padding-top: 10px; color: #333; }
    .faq-item.open .faq-answer { display: block; }

    /* ===== КОНТАКТЫ ===== */
    .contacts-row { display: flex; gap: 40px; flex-wrap: wrap; margin-top: 30px; }
    .contacts-row .info { flex: 1; }
    .contacts-row .form { flex: 2; }

    /* ===== ФУТЕР ===== */
    .footer {
      background: #0b1424;
      color: #aaa;
      padding: 40px 0;
      margin-top: 40px;
    }
    .footer .container { display: grid; grid-template-columns: 2fr 1fr 1fr; gap: 40px; }
    .footer a { color: #ccc; }
    .footer a:hover { color: #fff; }
    .socials { display: flex; gap: 16px; margin-top: 10px; }

    /* ===== АДАПТИВ ===== */
    @media (max-width: 900px) {
      .stats { grid-template-columns: repeat(2,1fr); }
      .grid-3 { grid-template-columns: 1fr 1fr; }
      .news-grid { grid-template-columns: 1fr 1fr; }
      .footer .container { grid-template-columns: 1fr; }
    }
    @media (max-width: 700px) {
      .nav { display: none; flex-direction: column; width: 100%; margin-top: 16px; }
      .nav.open { display: flex; }
      .burger { display: block; }
      .hero h1 { font-size: 32px; }
      .grid-3 { grid-template-columns: 1fr; }
      .news-grid { grid-template-columns: 1fr; }
      .stats { grid-template-columns: 1fr 1fr; }
      .contacts-row { flex-direction: column; }
    }
  </style>
</head>
<body>

<!-- ===== ШАПКА ===== -->
<header class="header">
  <div class="container">
    <div class="logo">#<span>Вместе</span>Восстановим</div>
    <button class="burger" id="burger">☰</button>
    <nav class="nav" id="nav">
      <a href="#" data-page="home" class="active">Главная</a>
      <a href="#" data-page="about">О проекте</a>
      <a href="#" data-page="news">Новости</a>
      <a href="#" data-page="help">Как помочь</a>
      <a href="#" data-page="support">Поддержка</a>
      <a href="#" data-page="recovery">Восстановление</a>
      <a href="#" data-page="faq">Библиотека</a>
11:37
<a href="#" data-page="contacts">Контакты</a>
      <a href="#" data-page="help" class="btn-donate">Помочь</a>
    </nav>
  </div>
</header>

<!-- ===== ГЛАВНАЯ ===== -->
<div id="home" class="page active">
  <div class="container">
    <div class="hero">
      <h1>Завод остановлен — мы не остановимся</h1>
      <p>Атака на НПЗ — удар по всей стране. Но враг просчитался: народ встал плечом к плечу. Тысячи уже помогают восстанавливать производство. Каждый рубль, каждый час работы приближает пуск завода и срывает планы противника. Присоединяйся!</p>
      <div class="hero-buttons">
        <a href="#" data-page="help" class="btn-primary">Перевести средства</a>
        <a href="#" data-page="help" class="btn-secondary">Стать волонтёром</a>
      </div>
      <div class="ticker" id="ticker">
        Собрано: <span id="sum">0</span> ₽ · Волонтёров: <span id="vol">0</span> · Восстановлено: <span id="pct">0</span>% · Дней без аварий: <span id="days">0</span>
      </div>
    </div>

    <div class="stats" id="stats">
      <div class="stat-card"><div class="number" data-count="47800000">0</div><div class="label">Собрано средств (₽)</div></div>
      <div class="stat-card"><div class="number" data-count="1250">0</div><div class="label">Волонтёров в строю</div></div>
      <div class="stat-card"><div class="number" data-count="63">0</div><div class="label">Восстановлено оборудования (%)</div></div>
      <div class="stat-card"><div class="number" data-count="42">0</div><div class="label">Дней без аварий</div></div>
    </div>

    <h2>Почему это важно</h2>
    <div class="grid-3">
      <div class="card"><h3>🤝  Единство</h3><p>Нас не разделить. Рабочие, инженеры, домохозяйки, студенты — все вносят свой вклад. Мы — одна сила.</p></div>
      <div class="card"><h3>⚙️  Восстановление</h3><p>Каждый день бригады трудятся в две смены. Уже запущены три агрегата, идёт подача топлива в регионы.</p></div>
      <div class="card"><h3>🇷🇺  Срыв планов врага</h3><p>Чем быстрее заработает завод, тем быстрее мы восстановим энергобезопасность и докажем: нас не сломить.</p></div>
    </div>

    <h2>Свежие новости</h2>
    <div class="news-grid">
      <div class="news-item"><img src="https://via.placeholder.com/400x200/0b1424/e85a2c?text=Новость+1" alt=""><div class="text"><div class="date">25.08.2026</div><h4>Запущен второй агрегат</h4><p>После 12-часовой работы бригада подключила компрессор.</p></div></div>
      <div class="news-item"><img src="https://via.placeholder.com/400x200/0b1424/2a5f8a?text=Новость+2" alt=""><div class="text"><div class="date">24.08.2026</div><h4>Волонтёры доставили 5 тонн запчастей</h4><p>Колонна из 8 машин прибыла на завод утром.</p></div></div>
      <div class="news-item"><img src="https://via.placeholder.com/400x200/0b1424/e85a2c?text=Новость+3" alt=""><div class="text"><div class="date">23.08.2026</div><h4>Открыт пункт психологической помощи</h4><p>Специалисты принимают семьи работников.</p></div></div>
    </div>
    <p style="text-align:right"><a href="#" data-page="news">Все новости →</a></p>

    <h2>Истории героев</h2>
    <div class="grid-3">
      <div class="card"><h3>Алексей, сварщик</h3><p>«Я не ушёл с поста, даже когда было страшно. Мы работаем за себя и за страну».</p></div>
      <div class="card"><h3>Мария, волонтёр-пенсионер</h3><p>«Приехала из Рязани, чтобы помочь. Своих не бросаем!»</p></div>
      <div class="card"><h3>Дмитрий, врач</h3><p>«Организовал медпункт прямо на объекте. Здоровье рабочих — наша задача».</p></div>
    </div>

    <h2>Как помочь прямо сейчас</h2>
    <div style="display:flex; gap:20px; flex-wrap:wrap; justify-content:space-around; margin:20px 0;">
      <a href="#" data-page="help" style="background:#fff; padding:16px 30px; border-radius:12px; box-shadow:0 2px 8px rgba(0,0,0,0.1);">💰 Деньги</a>
      <a href="#" data-page="help" style="background:#fff; padding:16px 30px; border-radius:12px; box-shadow:0 2px 8px rgba(0,0,0,0.1);">📦 Материалы</a>
11:37
<a href="#" data-page="help" style="background:#fff; padding:16px 30px; border-radius:12px; box-shadow:0 2px 8px rgba(0,0,0,0.1);">🛠️  Руки</a>
      <a href="#" data-page="help" style="background:#fff; padding:16px 30px; border-radius:12px; box-shadow:0 2px 8px rgba(0,0,0,0.1);">📢  Репост</a>
    </div>

    <div style="background:#fff; padding:30px; border-radius:16px;">
      <h3>Остались вопросы? Напишите нам</h3>
      <div class="form-group"><input type="text" placeholder="Ваше сообщение" /></div>
      <button class="btn-primary">Отправить</button>
    </div>
  </div>
</div>

<!-- ===== О ПРОЕКТЕ ===== -->
<div id="about" class="page">
  <div class="container">
    <h1>О нас</h1>
    <p><strong>Мы — гражданский штаб, созданный в первые часы после теракта.</strong> Наша цель — координировать помощь заводу и его работникам. Мы не чиновники и не политики. Мы — такие же, как вы. Нас объединила беда, и мы твёрдо решили: завод должен работать. Враг хотел посеять страх — а получил народное сопротивление. Мы докажем, что вместе мы сила.</p>
    <h2>Наша миссия</h2>
    <div class="grid-3">
      <div class="card"><h3>Сплочение</h3><p>Объединяем граждан, бизнес и власть вокруг одной задачи.</p></div>
      <div class="card"><h3>Восстановление</h3><p>Оперативно ремонтируем повреждённые агрегаты и инфраструктуру.</p></div>
      <div class="card"><h3>Победа</h3><p>Срываем планы противника, возвращаем стране топливную независимость.</p></div>
    </div>
    <h2>Команда</h2>
    <div style="display:flex; flex-wrap:wrap; gap:20px;">
      <div style="background:#fff; padding:20px; border-radius:12px; min-width:150px;"><strong>Руководитель штаба</strong><br>опыт более 20 лет</div>
      <div style="background:#fff; padding:20px; border-radius:12px; min-width:150px;"><strong>Главный инженер</strong><br>бывший замдиректора НПЗ</div>
      <div style="background:#fff; padding:20px; border-radius:12px; min-width:150px;"><strong>Координатор волонтёров</strong><br>организатор акций</div>
      <div style="background:#fff; padding:20px; border-radius:12px; min-width:150px;"><strong>Психолог</strong><br>работа с семьями</div>
    </div>
    <h2>Открытость</h2>
    <p>Мы отчитываемся каждую неделю: все поступления и расходы — в открытом доступе. Честность — наша основа.</p>
  </div>
</div>

<!-- ===== НОВОСТИ ===== -->
<div id="news" class="page">
  <div class="container">
    <h1>Новости восстановления</h1>
    <div class="tabs">
      <button class="tab-btn active" data-tab="all">Все</button>
      <button class="tab-btn" data-tab="repair">Ремонт</button>
      <button class="tab-btn" data-tab="volunteers">Волонтёры</button>
      <button class="tab-btn" data-tab="safety">Безопасность</button>
      <button class="tab-btn" data-tab="official">Официально</button>
    </div>
    <div class="news-grid" id="newsGrid">
      <!-- заполняется JS -->
    </div>
    <div style="margin-top:30px;">
      <h2>Видео дня</h2>
      <div style="background:#0b1424; color:#fff; padding:40px; border-radius:16px; text-align:center;">📹 Встраивание видео (YouTube)</div>
    </div>
    <div style="margin-top:30px;">
      <h2>Фото дня</h2>
      <img src="https://via.placeholder.com/1200x400/0b1424/e85a2c?text=Фото+дня:+установка+трансформатора" style="width:100%; border-radius:16px;" alt="Фото дня" />
      <p style="text-align:center; margin-top:8px;">Установка нового трансформатора. 26 августа 2026</p>
    </div>
  </div>
</div>

<!-- ===== КАК ПОМОЧЬ ===== -->
<div id="help" class="page">
  <div class="container">
    <h1>Помочь заводу — помочь стране</h1>
    <div class="tabs" id="helpTabs">
      <button class="tab-btn active" data-tab="finance">Финансовая</button>
      <button class="tab-btn" data-tab="materials">Материалы</button>
      <button class="tab-btn" data-tab="volunteer">Волонтёрство</button>
      <button class="tab-btn" data-tab="info">Информационная</button>
    </div>

    <!-- Финансовая -->
11:37
<div class="tab-content active" id="finance">
      <p>Даже небольшая сумма — это вклад в общее дело. Средства идут на закупку запчастей, топлива, питания для волонтёров и компенсации работникам. Переведите быстро и безопасно.</p>
      <div class="form-group"><label>Сумма (₽)</label><input type="number" value="1000" /></div>
      <div style="display:flex; gap:10px; flex-wrap:wrap;"><button class="tab-btn" style="background:#e0e6f0;">500</button><button class="tab-btn" style="background:#e0e6f0;">1000</button><button class="tab-btn" style="background:#e0e6f0;">5000</button><button class="tab-btn" style="background:#e0e6f0;">10000</button></div>
      <div class="form-group"><label>Назначение</label><select><option>Общий фонд</option><option>Конкретный агрегат</option><option>Помощь семьям</option></select></div>
      <div style="display:flex; gap:20px; flex-wrap:wrap; margin:16px 0;">💳 Visa  💳 Mir  📱  СБП  📱  QR-код</div>
      <div class="form-group"><input type="checkbox" id="anon" /> <label for="anon">Я согласен на публикацию в отчёте (можно анонимно)</label></div>
      <button class="btn-primary">Перевести</button>
      <h3>Последние пожертвования</h3>
      <table style="width:100%; border-collapse:collapse; background:#fff; border-radius:12px; overflow:hidden;">
        <tr style="background:#0b1424; color:#fff;"><th>Имя</th><th>Сумма</th><th>Дата</th></tr>
        <tr><td>Анна К.</td><td>5 000 ₽</td><td>26.08.2026</td></tr>
        <tr><td>ООО «ТрансСервис»</td><td>50 000 ₽</td><td>26.08.2026</td></tr>
        <tr><td>Владимир П.</td><td>1 000 ₽</td><td>25.08.2026</td></tr>
      </table>
    </div>

    <!-- Материалы -->
    <div class="tab-content" id="materials">
      <p>Заводу срочно нужны: насосы, трубы, кабель, масло, спецодежда. Посмотрите список и выберите, что можете передать.</p>
      <div style="background:#fff; padding:20px; border-radius:12px;">
        <div><input type="checkbox" /> Насосы (до 10 шт.)</div>
        <div><input type="checkbox" /> Трубы (100 м)</div>
        <div><input type="checkbox" /> Кабель (500 м)</div>
        <div><input type="checkbox" /> Трансформаторное масло</div>
        <div><input type="checkbox" /> Спецодежда (50 комплектов)</div>
        <button class="btn-secondary" style="margin-top:16px;">Предложить выбранное</button>
      </div>
      <div style="margin-top:20px;">📍  Карта пунктов приёма (Яндекс.Карты)</div>
    </div>

    <!-- Волонтёрство -->
    <div class="tab-content" id="volunteer">
      <p>Нужны руки — ваши руки. Заполните анкету, и мы свяжемся с вами в течение часа.</p>
      <div class="form-group"><label>ФИО</label><input type="text" /></div>
      <div class="form-group"><label>Возраст</label><input type="number" /></div>
      <div class="form-group"><label>Город</label><input type="text" /></div>
      <div class="form-group"><label>Контактный телефон</label><input type="tel" /></div>
      <div class="form-group"><label>Навыки</label><select><option>Сварщик</option><option>Водитель</option><option>Разнорабочий</option><option>Медик</option><option>Повар</option><option>Психолог</option><option>Связист</option></select></div>
      <div class="form-group"><label>Готовность к выезду</label><input type="checkbox" /> Да</div>
      <div class="form-group"><label>Доступное время</label><input type="text" placeholder="например, вечер после 18:00" /></div>
      <button class="btn-primary">Записаться</button>
    </div>

    <!-- Информационная -->
    <div class="tab-content" id="info">
      <p>Распространяйте правду. Скачивайте готовые посты и публикуйте в соцсетях. Каждый репост — это удар по дезинформации врага.</p>
      <button class="btn-secondary">📥 Скачать пак картинок и текстов</button>
      <div style="margin:20px 0;">Хештеги: <strong>#НПЗ #Вместе #СвоихНеБросаем</strong></div>
      <h3>Сообщить о фейке</h3>
      <div class="form-group"><textarea placeholder="Вставьте ссылку или описание"></textarea></div>
11:37
<button class="btn-primary">Отправить</button>
    </div>
  </div>
</div>

<!-- ===== ПОДДЕРЖКА ===== -->
<div id="support" class="page">
  <div class="container">
    <h1>Помощь работникам и их семьям</h1>
    <div style="background:#fff; padding:24px; border-radius:16px; margin-bottom:20px;">
      <h2>Для работников завода</h2>
      <p>Если вы потеряли имущество, здоровье или нуждаетесь в жилье — оформите заявку, и мы поможем. Также действует горячая линия и пункты временного размещения.</p>
      <button class="btn-primary">Подать заявку на помощь</button>
      <div style="margin-top:16px;">📞  Горячая линия: 8-800-XXX-XX-XX · МЧС · Администрация</div>
    </div>
    <div style="background:#fff; padding:24px; border-radius:16px; margin-bottom:20px;">
      <h2>Для семей</h2>
      <p>Жёны, дети, пожилые родители — вы не одни. Психологи и юристы работают ежедневно. Бесплатные консультации и гуманитарная помощь.</p>
      <button class="btn-secondary">Записаться к психологу</button>
      <div style="margin-top:16px;">📍  Пункты выдачи детских вещей, продуктов</div>
    </div>
    <div style="background:#fff; padding:24px; border-radius:16px;">
      <h2>Памятки по безопасности</h2>
      <p>Знание спасает жизнь. Ознакомьтесь с инструкциями и скачайте их на телефон.</p>
      <ul style="list-style:none; padding:0;">
        <li>🔹  При воздушной тревоге</li>
        <li>🔹  Осколочные ранения — первая помощь</li>
        <li>🔹  Безопасность окон</li>
      </ul>
      <button class="btn-secondary">Скачать все памятки (PDF)</button>
    </div>
  </div>
</div>

<!-- ===== ВОССТАНОВЛЕНИЕ ===== -->
<div id="recovery" class="page">
  <div class="container">
    <h1>Как идёт восстановление — отчёт в реальном времени</h1>
    <div class="timeline">
      <div class="timeline-item"><div class="date">20.06.2026</div><p>Расчистка завалов завершена.</p></div>
      <div class="timeline-item"><div class="date">01.07.2026</div><p>Подано электропитание на первую очередь.</p></div>
      <div class="timeline-item"><div class="date">15.07.2026</div><p>Запущен компрессорный цех.</p></div>
      <div class="timeline-item"><div class="date">10.08.2026</div><p>Начало поставок топлива в регион.</p></div>
      <div class="timeline-item"><div class="date">25.08.2026</div><p>Восстановление второго агрегата.</p></div>
    </div>
    <h2>Схема завода</h2>
    <div style="background:#0b1424; color:#fff; padding:40px; border-radius:16px; text-align:center; margin:20px 0;">
      🗺️  Интерактивная схема: зоны (красный — повреждён, жёлтый — частично, зелёный — работает)
    </div>
    <h2>Прогнозный график</h2>
    <div style="display:flex; gap:20px; justify-content:space-around; background:#fff; padding:24px; border-radius:16px;">
      <div><strong>1 этап (неделя)</strong><br>⚡ электроснабжение<br> <span style="color:#e85a2c;">100%</span></div>
      <div><strong>2 этап (месяц)</strong><br>🔧  50% мощностей<br> <span style="color:#e85a2c;">63%</span></div>
      <div><strong>3 этап (квартал)</strong><br>🏭 полная мощность<br> <span style="color:#e85a2c;">30%</span></div>
    </div>
  </div>
</div>

<!-- ===== БИБЛИОТЕКА / FAQ ===== -->
<div id="faq" class="page">
  <div class="container">
    <h1>Ответы на вопросы и полезные материалы</h1>
    <div class="faq-item open">
      <div class="faq-question">Как убедиться, что деньги пойдут именно на завод?</div>
      <div class="faq-answer">Мы публикуем все платёжные поручения и акты выполненных работ. Подробные отчёты — в разделе «Отчётность».</div>
    </div>
    <div class="faq-item">
      <div class="faq-question">Может ли волонтёр приехать из другого города?</div>
      <div class="faq-answer">Да, для иногородних предоставляется проживание в общежитии и питание. Записывайтесь в анкете.</div>
    </div>
    <div class="faq-item">
      <div class="faq-question">Что нужно для работы на объекте?</div>
11:37
<div class="faq-answer">Достаточно желания и отсутствия медицинских противопоказаний. Специалисты проведут инструктаж на месте.</div>
    </div>
    <div class="faq-item">
      <div class="faq-question">Как передать запчасти, если я далеко?</div>
      <div class="faq-answer">Отправьте через любую транспортную компанию до нашего склада, реквизиты указаны в разделе «Контакты».</div>
    </div>
    <h2>Скачать файлы</h2>
    <ul style="background:#fff; padding:20px; border-radius:12px; list-style:none;">
      <li>📄  Памятка волонтёра (PDF) — <a href="#">Скачать</a></li>
      <li>📄  Договор пожертвования (DOC) — <a href="#">Скачать</a></li>
      <li>📄  Заявление на компенсацию (PDF) — <a href="#">Скачать</a></li>
      <li>📄  Инструкция по ТБ (PDF) — <a href="#">Скачать</a></li>
    </ul>
    <h2>Полезные ссылки</h2>
    <ul>
      <li><a href="#">Минэнерго РФ</a></li>
      <li><a href="#">МЧС России</a></li>
      <li><a href="#">Администрация региона</a></li>
    </ul>
  </div>
</div>

<!-- ===== КОНТАКТЫ ===== -->
<div id="contacts" class="page">
  <div class="container">
    <h1>Свяжитесь с нами</h1>
    <div class="contacts-row">
      <div class="info">
        <p><strong>Горячая линия:</strong> 8-800-XXX-XX-XX (круглосуточно)</p>
        <p><strong>E-mail:</strong> help@npz-spasenie.ru</p>
        <p><strong>Telegram:</strong> @npz_help</p>
        <p><strong>ВКонтакте:</strong> vk.com/npz_spasenie</p>
        <p><strong>Адрес штаба:</strong> г. Москва, ул. Примерная, д. 1</p>
        <div style="margin-top:10px;">📍  Карта проезда</div>
      </div>
      <div class="form">
        <div class="form-group"><label>Имя</label><input type="text" /></div>
        <div class="form-group"><label>E-mail или телефон</label><input type="text" /></div>
        <div class="form-group"><label>Тема</label><input type="text" /></div>
        <div class="form-group"><label>Сообщение</label><textarea></textarea></div>
        <button class="btn-primary">Отправить</button>
      </div>
    </div>
  </div>
</div>

<!-- ===== ФУТЕР ===== -->
<footer class="footer">
  <div class="container">
    <div>
      <div style="color:#fff; font-size:20px;">#ВместеВосстановим</div>
      <p style="margin-top:10px;">© 2026 Гражданский штаб помощи</p>
      <p>Все средства направляются адресно.</p>
    </div>
    <div>
      <h4 style="color:#fff;">Меню</h4>
      <a href="#" data-page="home">Главная</a><br />
      <a href="#" data-page="about">О проекте</a><br />
      <a href="#" data-page="help">Как помочь</a><br />
      <a href="#" data-page="contacts">Контакты</a>
    </div>
    <div>
      <h4 style="color:#fff;">Мы в соцсетях</h4>
      <div class="socials">
        <a href="#">📱  Telegram</a>
        <a href="#">📘  ВК</a>
        <a href="#">📸  ОК</a>
      </div>
    </div>
  </div>
</footer>

<!-- ===== JAVASCRIPT ===== -->
<script>
  (function() {
    // ----- Навигация -----
    const pages = document.querySelectorAll('.page');
    const navLinks = document.querySelectorAll('.nav a[data-page]');
    const burger = document.getElementById('burger');
    const nav = document.getElementById('nav');

    function showPage(pageId) {
      pages.forEach(p => p.classList.remove('active'));
      document.getElementById(pageId).classList.add('active');
      navLinks.forEach(a => a.classList.remove('active'));
      document.querySelector(`.nav a[data-page="${pageId}"]`)?.classList.add('active');
      // Закрыть меню на мобильных
      nav.classList.remove('open');
      // скролл наверх
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    navLinks.forEach(link => {
      link.addEventListener('click', function(e) {
        e.preventDefault();
        const page = this.dataset.page;
        showPage(page);
        // если это кнопка "Помочь" - переключаем на help
        if (this.classList.contains('btn-donate')) {
          showPage('help');
        }
      });
    });

    burger.addEventListener('click', function() {
11:37
nav.classList.toggle('open');
    });

    // ----- Вкладки внутри "Как помочь" -----
    const helpTabs = document.querySelectorAll('#helpTabs .tab-btn');
    const helpContents = document.querySelectorAll('#help .tab-content');

    helpTabs.forEach(btn => {
      btn.addEventListener('click', function() {
        helpTabs.forEach(b => b.classList.remove('active'));
        this.classList.add('active');
        const tab = this.dataset.tab;
        helpContents.forEach(c => c.classList.remove('active'));
        document.getElementById(tab).classList.add('active');
      });
    });

    // ----- Вкладки в новостях (демо) -----
    const newsTabs = document.querySelectorAll('#news .tabs .tab-btn');
    const newsGrid = document.getElementById('newsGrid');
    // просто для примера при клике меняем заглушки
    newsTabs.forEach(btn => {
      btn.addEventListener('click', function() {
        newsTabs.forEach(b => b.classList.remove('active'));
        this.classList.add('active');
        const tab = this.dataset.tab;
        const fakeText = tab === 'all' ? 'Все новости' : tab === 'repair' ? 'Ремонт' : tab === 'volunteers' ? 'Волонтёры' : tab === 'safety' ? 'Безопасность' : 'Официально';
        newsGrid.innerHTML = `<div class="news-item"><img src="https://via.placeholder.com/400x200/0b1424/e85a2c?text=${fakeText}" alt=""><div class="text"><div class="date">26.08.2026</div><h4>Новости по теме «${fakeText}»</h4><p>Здесь будут статьи.</p></div></div>`;
      });
    });
    // Инициализация новостей
    document.querySelector('#news .tabs .tab-btn.active')?.click();

    // ----- FAQ аккордеон -----
    document.querySelectorAll('.faq-question').forEach(q => {
      q.addEventListener('click', function() {
        const item = this.parentElement;
        item.classList.toggle('open');
      });
    });

    // ----- Анимация счётчиков (скролл) -----
    function animateCounters() {
      const counters = document.querySelectorAll('.stat-card .number');
      const windowHeight = window.innerHeight;
      counters.forEach(counter => {
        const rect = counter.getBoundingClientRect();
        if (rect.top < windowHeight - 50 && !counter.dataset.animated) {
          counter.dataset.animated = 'true';
          const target = parseInt(counter.dataset.count, 10);
          let current = 0;
          const step = Math.max(1, Math.floor(target / 60));
          const interval = setInterval(() => {
            current += step;
            if (current >= target) {
              current = target;
              clearInterval(interval);
            }
            // Форматирование для больших чисел
            if (target > 1000000) {
              counter.textContent = current.toLocaleString('ru-RU');
            } else {
              counter.textContent = current;
            }
          }, 20);
        }
      });
    }

    // Обновление бегущей строки (заглушка)
    function updateTicker() {
      const sum = document.getElementById('sum');
      const vol = document.getElementById('vol');
      const pct = document.getElementById('pct');
      const days = document.getElementById('days');
      // случайные изменения для демонстрации
      setInterval(() => {
        const baseSum = 47800000;
        const add = Math.floor(Math.random() * 100000);
        sum.textContent = (baseSum + add).toLocaleString('ru-RU');
        vol.textContent = 1250 + Math.floor(Math.random() * 20);
        pct.textContent = 63 + Math.floor(Math.random() * 5);
        days.textContent = 42 + Math.floor(Math.random() * 3);
      }, 8000);
    }

    window.addEventListener('load', function() {
      animateCounters();
      updateTicker();
    });
    window.addEventListener('scroll', animateCounters);
    window.addEventListener('resize', animateCounters);

    // Переключение на главную по умолчанию (уже активна)
  })();
</script>

</body>
</html>

<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Rent-A-Girlfriend · 借用女友</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=Noto+Serif+SC:wght@400;700;900&family=JetBrains+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    font-family: 'Noto Serif SC', 'Playfair Display', serif;
    background: #0A0A0F;
    color: #FAF6F0;
    overflow-x: hidden;
    line-height: 1.6;
  }
  .mono { font-family: 'JetBrains Mono', monospace; }

  /* ========== NAV ========== */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 100;
    display: flex; justify-content: space-between; align-items: center;
    padding: 20px 60px;
    background: rgba(10, 10, 15, 0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(212, 165, 116, 0.15);
  }
  .logo {
    font-family: 'Playfair Display', serif;
    font-size: 26px; font-weight: 900;
    color: #D4A574; letter-spacing: 2px;
  }
  .logo span { color: #FF3E7F; }
  .nav-links { display: flex; gap: 40px; }
  .nav-links a {
    color: #FAF6F0; text-decoration: none;
    font-size: 14px; letter-spacing: 1px;
    transition: color 0.3s;
  }
  .nav-links a:hover { color: #D4A574; }
  .nav-cta {
    padding: 10px 24px;
    background: #FF3E7F; color: #fff;
    border-radius: 30px; font-size: 13px;
    letter-spacing: 1px; text-decoration: none;
    box-shadow: 0 0 20px rgba(255, 62, 127, 0.4);
    transition: all 0.3s;
  }
  .nav-cta:hover { transform: scale(1.05); box-shadow: 0 0 30px rgba(255, 62, 127, 0.7); }

  /* ========== HERO ========== */
  .hero {
    min-height: 100vh;
    display: flex; flex-direction: column; justify-content: center; align-items: center;
    text-align: center;
    padding: 120px 40px 60px;
    background: radial-gradient(ellipse at center, #2D1B3D 0%, #0A0A0F 70%);
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; top: 50%; left: 50%;
    width: 800px; height: 800px;
    transform: translate(-50%, -50%);
    background: radial-gradient(circle, rgba(212, 165, 116, 0.08) 0%, transparent 70%);
    border-radius: 50%;
    animation: pulse 6s infinite ease-in-out;
  }
  @keyframes pulse {
    0%, 100% { transform: translate(-50%, -50%) scale(1); opacity: 0.5; }
    50% { transform: translate(-50%, -50%) scale(1.1); opacity: 0.8; }
  }
  .hero-tag {
    font-size: 12px; letter-spacing: 6px;
    color: #D4A574; margin-bottom: 30px;
    text-transform: uppercase;
    position: relative; z-index: 2;
  }
  .hero h1 {
    font-family: 'Playfair Display', 'Noto Serif SC', serif;
    font-size: clamp(48px, 8vw, 96px);
    font-weight: 900;
    color: #FAF6F0;
    margin-bottom: 20px;
    line-height: 1.1;
    position: relative; z-index: 2;
  }
  .hero h2 {
    font-family: 'Playfair Display', 'Noto Serif SC', serif;
    font-size: clamp(36px, 6vw, 72px);
    font-weight: 700;
    color: #FF3E7F;
    font-style: italic;
    margin-bottom: 50px;
    position: relative; z-index: 2;
  }
  .hero-sub {
    font-size: 16px; color: #999;
    max-width: 500px; margin-bottom: 40px;
    letter-spacing: 1px;
    position: relative; z-index: 2;
  }
  .cta-main {
    display: inline-block;
    padding: 18px 60px;
    background: #FF3E7F; color: #fff;
    font-size: 16px; letter-spacing: 3px;
    text-decoration: none; border-radius: 50px;
    box-shadow: 0 0 40px rgba(255, 62, 127, 0.5);
    transition: all 0.3s;
    position: relative; z-index: 2;
    animation: heartbeat 2s infinite;
  }
  @keyframes heartbeat {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.03); }
  }
  .cta-main:hover { transform: scale(1.08); box-shadow: 0 0 60px rgba(255, 62, 127, 0.8); }
  .cta-note {
    margin-top: 20px; font-size: 12px;
    color: #666; letter-spacing: 2px;
    font-style: italic;
    position: relative; z-index: 2;
  }

  /* ========== SECTION COMMON ========== */
  section { padding: 120px 60px; }
  .section-tag {
    display: block; text-align: center;
    color: #D4A574; font-size: 12px;
    letter-spacing: 8px; margin-bottom: 20px;
    text-transform: uppercase;
  }
  .section-title {
    font-family: 'Playfair Display', 'Noto Serif SC', serif;
    text-align: center;
    font-size: clamp(36px, 5vw, 60px);
    font-weight: 900;
    margin-bottom: 80px;
    color: #FAF6F0;
  }
  .section-title em {
    color: #FF3E7F; font-style: italic;
  }

  /* ========== FEATURES ========== */
  .features {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 40px;
    max-width: 1200px; margin: 0 auto;
  }
  .feature-card {
    background: linear-gradient(180deg, rgba(212, 165, 116, 0.05) 0%, transparent 100%);
    border: 1px solid rgba(212, 165, 116, 0.15);
    padding: 50px 40px; border-radius: 20px;
    text-align: center;
    transition: all 0.4s;
  }
  .feature-card:hover {
    transform: translateY(-10px);
    border-color: rgba(212, 165, 116, 0.4);
    background: linear-gradient(180deg, rgba(212, 165, 116, 0.1) 0%, transparent 100%);
  }
  .feature-icon {
    font-size: 48px; margin-bottom: 25px;
    display: inline-block;
  }
  .feature-title {
    font-size: 24px; color: #D4A574;
    margin-bottom: 20px; letter-spacing: 2px;
    font-weight: 700;
  }
  .feature-desc {
    color: #aaa; font-size: 15px;
    line-height: 1.8;
  }

  /* ========== STATS ========== */
  .stats-section {
    background: linear-gradient(180deg, #0A0A0F 0%, #2D1B3D 50%, #0A0A0F 100%);
    border-top: 1px solid rgba(212, 165, 116, 0.1);
    border-bottom: 1px solid rgba(212, 165, 116, 0.1);
  }
  .stats-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 40px;
    max-width: 1200px; margin: 0 auto;
  }
  .stat-item { text-align: center; }
  .stat-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: clamp(36px, 4vw, 56px);
    font-weight: 700;
    color: #D4A574;
    margin-bottom: 10px;
    text-shadow: 0 0 20px rgba(212, 165, 116, 0.3);
  }
  .stat-label {
    font-size: 12px; color: #888;
    letter-spacing: 3px;
    text-transform: uppercase;
  }

  /* ========== CATALOG ========== */
  .catalog {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 30px;
    max-width: 1300px; margin: 0 auto;
  }
  .girl-card {
    background: #14141c;
    border: 1px solid rgba(212, 165, 116, 0.15);
    border-radius: 20px;
    overflow: hidden;
    transition: all 0.4s;
    cursor: pointer;
  }
  .girl-card:hover {
    transform: translateY(-8px);
    border-color: #D4A574;
    box-shadow: 0 20px 60px rgba(212, 165, 116, 0.15);
  }
  .girl-photo {
    height: 320px;
    background: linear-gradient(135deg, #3d2645 0%, #1a0f24 100%);
    position: relative;
    display: flex; justify-content: center; align-items: center;
    overflow: hidden;
  }
  .girl-silhouette {
    width: 200px; height: 280px;
    background: linear-gradient(180deg, rgba(255, 255, 255, 0.15) 0%, rgba(255, 255, 255, 0.05) 100%);
    border-radius: 100px 100px 20px 20px;
    position: relative;
  }
  .girl-silhouette::before {
    content: '';
    position: absolute;
    top: 20px; left: 50%;
    transform: translateX(-50%);
    width: 80px; height: 100px;
    background: linear-gradient(135deg, #D4A574 0%, #8b6b4a 100%);
    border-radius: 50%;
    box-shadow: 0 0 40px rgba(212, 165, 116, 0.4);
  }
  .girl-mask {
    position: absolute; top: 40px; left: 50%;
    transform: translateX(-50%);
    padding: 4px 12px;
    background: rgba(212, 165, 116, 0.9);
    color: #0A0A0F;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px; font-weight: 700;
    border-radius: 20px;
    letter-spacing: 1px;
  }
  .girl-status {
    position: absolute; top: 15px; right: 15px;
    padding: 6px 12px;
    background: rgba(0, 0, 0, 0.7);
    border-radius: 20px;
    font-size: 11px;
    letter-spacing: 1px;
    display: flex; align-items: center; gap: 6px;
  }
  .status-dot {
    width: 8px; height: 8px; border-radius: 50%;
    animation: blink 1.5s infinite;
  }
  .status-online .status-dot { background: #4ade80; }
  .status-busy .status-dot { background: #FF3E7F; }
  @keyframes blink { 50% { opacity: 0.3; } }
  .girl-tags {
    position: absolute; bottom: 15px; left: 15px;
    display: flex; gap: 6px; flex-wrap: wrap;
  }
  .girl-tag {
    padding: 4px 10px;
    background: rgba(255, 62, 127, 0.9);
    color: #fff;
    font-size: 10px;
    border-radius: 12px;
    letter-spacing: 1px;
  }
  .girl-tag.gold { background: rgba(212, 165, 116, 0.9); color: #0A0A0F; }
  .girl-info { padding: 25px; }
  .girl-name {
    font-size: 20px; color: #FAF6F0;
    margin-bottom: 8px;
    display: flex; justify-content: space-between; align-items: center;
  }
  .girl-id { font-family: 'JetBrains Mono', monospace; font-size: 12px; color: #D4A574; }
  .girl-meta {
    color: #888; font-size: 13px;
    margin-bottom: 15px;
    letter-spacing: 0.5px;
  }
  .girl-rating {
    display: flex; align-items: center; gap: 10px;
    margin-bottom: 15px;
    font-size: 13px;
  }
  .stars { color: #D4A574; }
  .rating-count { color: #666; }
  .girl-beta {
    padding: 12px;
    background: rgba(255, 255, 255, 0.03);
    border-left: 3px solid #666;
    border-radius: 4px;
    margin-bottom: 20px;
    font-size: 12px;
    color: #777;
  }
  .girl-beta strong { color: #999; }
  .girl-price {
    display: flex; justify-content: space-between; align-items: baseline;
    margin-bottom: 20px;
  }
  .price-main {
    color: #FF3E7F;
    font-family: 'JetBrains Mono', monospace;
    font-size: 24px; font-weight: 700;
  }
  .price-unit { color: #666; font-size: 12px; margin-left: 4px; }
  .price-night { color: #888; font-size: 13px; }
  .girl-btn {
    display: block; text-align: center;
    padding: 12px; width: 100%;
    background: #FF3E7F; color: #fff;
    border: none; border-radius: 30px;
    font-size: 13px; letter-spacing: 2px;
    cursor: pointer;
    transition: all 0.3s;
    text-decoration: none;
  }
  .girl-btn:hover { background: #ff5c94; box-shadow: 0 0 25px rgba(255, 62, 127, 0.5); }

  /* ========== REVIEWS ========== */
  .reviews-section { background: #08080c; }
  .reviews {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 30px;
    max-width: 1200px; margin: 0 auto;
  }
  .review-card {
    background: linear-gradient(180deg, rgba(212, 165, 116, 0.05) 0%, transparent 100%);
    border: 1px solid rgba(212, 165, 116, 0.15);
    padding: 35px;
    border-radius: 16px;
  }
  .review-stars {
    color: #D4A574;
    font-size: 18px; margin-bottom: 15px;
    letter-spacing: 2px;
  }
  .review-text {
    color: #ccc; font-size: 15px;
    line-height: 1.8; margin-bottom: 20px;
    font-style: italic;
  }
  .review-author {
    color: #888; font-size: 12px;
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 1px;
  }

  /* ========== MEMBERSHIP ========== */
  .memberships {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 20px;
    max-width: 1300px; margin: 0 auto;
  }
  .member-card {
    background: #14141c;
    border: 1px solid rgba(212, 165, 116, 0.15);
    padding: 40px 30px;
    border-radius: 20px;
    text-align: center;
    transition: all 0.4s;
  }
  .member-card.featured {
    background: linear-gradient(180deg, rgba(255, 62, 127, 0.1) 0%, rgba(212, 165, 116, 0.05) 100%);
    border-color: #FF3E7F;
    transform: scale(1.05);
  }
  .member-card:hover { transform: translateY(-8px); }
  .member-card.featured:hover { transform: scale(1.05) translateY(-8px); }
  .member-tier {
    font-size: 14px; letter-spacing: 4px;
    color: #D4A574; margin-bottom: 10px;
  }
  .member-name {
    font-size: 28px; color: #FAF6F0;
    margin-bottom: 20px;
    font-weight: 700;
  }
  .member-price {
    font-family: 'JetBrains Mono', monospace;
    font-size: 32px; color: #FF3E7F;
    margin-bottom: 30px;
  }
  .member-price small {
    display: block;
    font-size: 12px; color: #666;
    letter-spacing: 2px;
    margin-top: 5px;
  }
  .member-perks {
    list-style: none;
    text-align: left;
    margin-bottom: 30px;
  }
  .member-perks li {
    padding: 10px 0;
    border-bottom: 1px solid rgba(255, 255, 255, 0.05);
    color: #aaa;
    font-size: 13px;
    padding-left: 20px;
    position: relative;
  }
  .member-perks li::before {
    content: '✓';
    position: absolute;
    left: 0; color: #D4A574;
  }

  /* ========== NOTICE / BETA WARNING ========== */
  .beta-notice {
    background: linear-gradient(135deg, #2D1B3D 0%, #0A0A0F 100%);
    padding: 100px 60px;
    text-align: center;
    border-top: 1px solid rgba(255, 62, 127, 0.2);
    border-bottom: 1px solid rgba(255, 62, 127, 0.2);
  }
  .beta-notice-title {
    font-family: 'Playfair Display', 'Noto Serif SC', serif;
    font-size: clamp(28px, 4vw, 48px);
    color: #FF3E7F;
    margin-bottom: 30px;
    font-style: italic;
  }
  .beta-notice-text {
    max-width: 700px; margin: 0 auto;
    color: #888; font-size: 16px;
    line-height: 2;
    letter-spacing: 1px;
  }
  .beta-notice-text strong {
    color: #D4A574;
    font-weight: 700;
  }

  /* ========== FOOTER ========== */
  footer {
    padding: 60px; text-align: center;
    background: #050508;
    border-top: 1px solid rgba(212, 165, 116, 0.1);
  }
  .footer-slogan {
    font-family: 'Playfair Display', 'Noto Serif SC', serif;
    font-size: 20px;
    color: #D4A574;
    margin-bottom: 30px;
    font-style: italic;
  }
  .footer-links {
    display: flex; justify-content: center; gap: 40px;
    margin-bottom: 30px;
    flex-wrap: wrap;
  }
  .footer-links a {
    color: #666; text-decoration: none;
    font-size: 12px; letter-spacing: 2px;
  }
  .footer-links a:hover { color: #D4A574; }
  .copyright {
    color: #444; font-size: 11px;
    letter-spacing: 2px;
    font-family: 'JetBrains Mono', monospace;
  }

  /* ========== RESPONSIVE ========== */
  @media (max-width: 900px) {
    nav { padding: 15px 20px; }
    .nav-links { display: none; }
    section { padding: 80px 20px; }
    .features, .catalog, .reviews, .memberships { grid-template-columns: 1fr; }
    .stats-grid { grid-template-columns: repeat(2, 1fr); }
    .member-card.featured { transform: none; }
  }
</style>
</head>
<body>

<!-- ============ NAV ============ -->
<nav>
  <div class="logo">RAG<span>·</span></div>
  <div class="nav-links">
    <a href="#home">首页</a>
    <a href="#browse">浏览女友</a>
    <a href="#membership">会员计划</a>
    <a href="#about">关于我们</a>
  </div>
  <a href="#" class="nav-cta">ALPHA 专属通道 →</a>
</nav>

<!-- ============ HERO ============ -->
<section class="hero" id="home">
  <div class="hero-tag">— RENT-A-GIRLFRIEND · SINCE 2021 —</div>
  <h1>她的男朋友<br>配不上她。</h1>
  <h2>But you can.</h2>
  <p class="hero-sub">全球首个Alpha专属·优质伴侣租借平台<br>让每一个优秀的基因，都不再被浪费。</p>
  <a href="#browse" class="cta-main">开 始 租 借 →</a>
  <p class="cta-note">* 仅限通过基因认证的Alpha级用户 · Beta请自行退出</p>
</section>

<!-- ============ FEATURES ============ -->
<section>
  <span class="section-tag">— why choose us —</span>
  <h2 class="section-title">为什么是<em>我们</em></h2>
  <div class="features">
    <div class="feature-card">
      <div class="feature-icon">🔍</div>
      <h3 class="feature-title">精准匹配</h3>
      <p class="feature-desc">根据您的练习需求、基因偏好、体格条件，为您匹配最契合的伴侣单元。每一次租借，都是量身定制。</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🌹</div>
      <h3 class="feature-title">真实体验</h3>
      <p class="feature-desc">不是充气娃娃，不是陪玩服务。是<em>真实的、有血有肉的、有男朋友的女性</em>——带着她的温度、她的反应、她的爱。</p>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🔄</div>
      <h3 class="feature-title">完璧归还</h3>
      <p class="feature-desc">使用完毕后，我们负责清理、护理、送回。她的Beta伴侣，不会察觉任何异常。除非——您想让他知道。</p>
    </div>
  </div>
</section>

<!-- ============ STATS ============ -->
<section class="stats-section">
  <span class="section-tag">— live data —</span>
  <h2 class="section-title">平台<em>实时数据</em></h2>
  <div class="stats-grid">
    <div class="stat-item">
      <div class="stat-num">12,847</div>
      <div class="stat-label">上架伴侣单元</div>
    </div>
    <div class="stat-item">
      <div class="stat-num">3,291</div>
      <div class="stat-label">Alpha 认证会员</div>
    </div>
    <div class="stat-item">
      <div class="stat-num">284,573</div>
      <div class="stat-label">累计租借次数</div>
    </div>
    <div class="stat-item">
      <div class="stat-num">0.02%</div>
      <div class="stat-label">Beta 察觉率</div>
    </div>
  </div>
</section>

<!-- ============ CATALOG ============ -->
<section id="browse">
  <span class="section-tag">— hot picks this week —</span>
  <h2 class="section-title">本周<em>热门伴侣</em></h2>
  <div class="catalog">

    <div class="girl-card">
      <div class="girl-photo">
        <div class="girl-silhouette"></div>
        <div class="girl-mask">#F-0847</div>
        <div class="girl-status status-online"><span class="status-dot"></span>在线</div>
        <div class="girl-tags">
          <span class="girl-tag gold">热门</span>
          <span class="girl-tag">内射可</span>
        </div>
      </div>
      <div class="girl-info">
        <div class="girl-name">小葵 <span class="girl-id">#F-0847</span></div>
        <div class="girl-meta">24岁 · 165cm · 86/60/88 · 市场专员</div>
        <div class="girl-rating">
          <span class="stars">★★★★★</span>
          <span>4.9</span>
          <span class="rating-count">(2,341 评价)</span>
        </div>
        <div class="girl-beta">
          <strong>Beta伴侣</strong>：#B-7734 · 168cm · 月入¥6,800<br>
          察觉状态：<strong>完全不知情</strong> · 恋爱4年3个月
        </div>
        <div class="girl-price">
          <div><span class="price-main">¥880</span><span class="price-unit">/小时</span></div>
          <div class="price-night">过夜 ¥3,880</div>
        </div>
        <a href="#" class="girl-btn">立 即 预 约 →</a>
      </div>
    </div>

    <div class="girl-card">
      <div class="girl-photo">
        <div class="girl-silhouette"></div>
        <div class="girl-mask">#F-0923</div>
        <div class="girl-status status-busy"><span class="status-dot"></span>使用中</div>
        <div class="girl-tags">
          <span class="girl-tag">最抢手</span>
          <span class="girl-tag gold">Beta同居</span>
        </div>
      </div>
      <div class="girl-info">
        <div class="girl-name">宁宁 <span class="girl-id">#F-0923</span></div>
        <div class="girl-meta">26岁 · 168cm · 88/62/90 · 平面设计师</div>
        <div class="girl-rating">
          <span class="stars">★★★★★</span>
          <span>4.95</span>
          <span class="rating-count">(1,872 评价)</span>
        </div>
        <div class="girl-beta">
          <strong>Beta伴侣</strong>：#B-4412 · 165cm · 刚被公司裁员<br>
          察觉状态：<strong>完全不知情</strong> · 已订婚
        </div>
        <div class="girl-price">
          <div><span class="price-main">¥1,280</span><span class="price-unit">/小时</span></div>
          <div class="price-night">过夜 ¥5,880</div>
        </div>
        <a href="#" class="girl-btn">加入等候名单 →</a>
      </div>
    </div>

    <div class="girl-card">
      <div class="girl-photo">
        <div class="girl-silhouette"></div>
        <div class="girl-mask">#F-1102</div>
        <div class="girl-status status-online"><span class="status-dot"></span>在线</div>
        <div class="girl-tags">
          <span class="girl-tag">新人</span>
          <span class="girl-tag gold">学生装</span>
        </div>
      </div>
      <div class="girl-info">
        <div class="girl-name">小鹿 <span class="girl-id">#F-1102</span></div>
        <div class="girl-meta">21岁 · 162cm · 82/58/85 · 大三在读</div>
        <div class="girl-rating">
          <span class="stars">★★★★★</span>
          <span>4.87</span>
          <span class="rating-count">(412 评价)</span>
        </div>
        <div class="girl-beta">
          <strong>Beta伴侣</strong>：#B-9981 · 172cm · 校友<br>
          察觉状态：<strong>完全不知情</strong> · 初恋
        </div>
        <div class="girl-price">
          <div><span class="price-main">¥680</span><span class="price-unit">/小时</span></div>
          <div class="price-night">过夜 ¥2,880</div>
        </div>
        <a href="#" class="girl-btn">立 即 预 约 →</a>
      </div>
    </div>

  </div>
</section>

<!-- ============ REVIEWS ============ -->
<section class="reviews-section">
  <span class="section-tag">— alpha testimonials —</span>
  <h2 class="section-title">Alpha <em>真实评价</em></h2>
  <div class="reviews">
    <div class="review-card">
      <div class="review-stars">★★★★★</div>
      <p class="review-text">"第一次租借就成功让她高潮三次。回来自己女朋友都能明显感觉到我技术变好了。比看AV学习有效多了。"</p>
      <div class="review-author">— Alpha #A-0231 · 铜卡会员</div>
    </div>
    <div class="review-card">
      <div class="review-stars">★★★★★</div>
      <p class="review-text">"叫床超甜，会主动叫'老公'。那种沉浸感是买不到的。她男朋友听不到，可惜了。下次买旁白服务发给他。"</p>
      <div class="review-author">— Alpha #A-0417 · 银卡会员</div>
    </div>
    <div class="review-card">
      <div class="review-stars">★★★★★</div>
      <p class="review-text">"上个月内射了她三次，这个月听说她怀了。孩子归她男朋友养。哈哈哈，绝了。五星好评。"</p>
      <div class="review-author">— Alpha #A-0089 · 金卡会员</div>
    </div>
  </div>
</section>

<!-- ============ MEMBERSHIP ============ -->
<section id="membership">
  <span class="section-tag">— membership plans —</span>
  <h2 class="section-title">Alpha <em>会员等级</em></h2>
  <div class="memberships">

    <div class="member-card">
      <div class="member-tier">— TIER 01 —</div>
      <div class="member-name">铜卡</div>
      <div class="member-price">¥12,800<small>/ 年</small></div>
      <ul class="member-perks">
        <li>每月租借上限 5 次</li>
        <li>标准伴侣库访问</li>
        <li>基础配种服务</li>
        <li>7×24 客服</li>
      </ul>
      <a href="#" class="girl-btn">申请开通</a>
    </div>

    <div class="member-card">
      <div class="member-tier">— TIER 02 —</div>
      <div class="member-name">银卡</div>
      <div class="member-price">¥38,800<small>/ 年</small></div>
      <ul class="member-perks">
        <li>每月租借上限 15 次</li>
        <li>高分伴侣库访问 (4.8+)</li>
        <li>可指定服装/道具</li>
        <li>免费剪辑视频 (5次)</li>
      </ul>
      <a href="#" class="girl-btn">申请开通</a>
    </div>

    <div class="member-card featured">
      <div class="member-tier" style="color:#FF3E7F">— MOST POPULAR —</div>
      <div class="member-name">金卡</div>
      <div class="member-price">¥88,800<small>/ 年</small></div>
      <ul class="member-perks">
        <li>不限次数租借</li>
        <li>全部伴侣库访问</li>
        <li>"配种成功"包月保障</li>
        <li>优先预约通道</li>
        <li>Beta男通知服务 · 半价</li>
      </ul>
      <a href="#" class="girl-btn">立即申请 →</a>
    </div>

    <div class="member-card">
      <div class="member-tier">— TIER 04 —</div>
      <div class="member-name">黑卡</div>
      <div class="member-price">¥288,800<small>/ 年</small></div>
      <ul class="member-perks">
        <li>定制专属伴侣</li>
        <li>包含Beta男通知服务</li>
        <li>DNA意外揭示服务</li>
        <li>私人剪辑师</li>
        <li>专属AI闺蜜旁白</li>
      </ul>
      <a href="#" class="girl-btn">邀请制申请</a>
    </div>

  </div>
</section>

<!-- ============ BETA NOTICE ============ -->
<section class="beta-notice" id="about">
  <h2 class="beta-notice-title">"我们不是在破坏关系。"</h2>
  <p class="beta-notice-text">
    Rent-A-Girlfriend 成立于 2021 年。<br>
    我们观察到一个残酷的社会现象——<br><br>
    <strong>优质的男性缺乏练习对象，<br>而优质的女性，被劣质的男性绑定。</strong><br><br>
    于是我们决定，做一个平台。<br>
    让优秀的基因流动起来。<br>
    让每一个Alpha，都能找到练习的伙伴。<br>
    让每一个被Beta绑定的优质女性，<br>都能重新体验到——被真正的男人操，是什么感觉。<br><br>
    <strong>我们不是在破坏关系。<br>我们是在修复自然选择。</strong>
  </p>
</section>

<!-- ============ FOOTER ============ -->
<footer>
  <p class="footer-slogan">"她的每一次呼吸，都是为了让你成为更好的男人。"</p>
  <div class="footer-links">
    <a href="#">使用条款</a>
    <a href="#">隐私政策</a>
    <a href="#">Alpha认证</a>
    <a href="#">Beta举报（受理率 0%）</a>
    <a href="#">联系我们</a>
  </div>
  <p class="copyright">© 2021—2025 RENT-A-GIRLFRIEND · ALL RIGHTS RESERVED · FOR ALPHA USE ONLY</p>
</footer>

</body>
</html>

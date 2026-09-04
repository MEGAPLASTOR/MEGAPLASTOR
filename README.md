<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Đinh Tấn Đạt — Developer</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg: #12121c;
    --panel: #191927;
    --panel-2: #1f1f30;
    --line: #2a2a3d;
    --gold: #e3a53d;
    --pink: #ef9fc0;
    --text: #f3efe4;
    --muted: #8d89a3;
  }

  *{ box-sizing: border-box; }

  html{ scroll-behavior: smooth; }

  body{
    margin: 0;
    background: var(--bg);
    background-image:
      radial-gradient(circle at 85% -5%, rgba(227,165,61,0.10), transparent 40%),
      radial-gradient(circle at 5% 15%, rgba(239,159,192,0.07), transparent 35%);
    color: var(--text);
    font-family: 'Space Grotesk', sans-serif;
    -webkit-font-smoothing: antialiased;
  }

  @media (prefers-reduced-motion: reduce){
    *{ animation: none !important; transition: none !important; }
  }

  a{ color: inherit; }

  .wrap{
    max-width: 980px;
    margin: 0 auto;
    padding: 0 32px;
  }

  /* ---------- NAV ---------- */
  .nav{
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 28px 0;
  }
  .nav .mark{
    font-family: 'JetBrains Mono', monospace;
    font-size: 14px;
    color: var(--muted);
    letter-spacing: 0.02em;
  }
  .nav .mark b{ color: var(--gold); font-weight: 500; }
  .nav-links{
    display: flex;
    gap: 28px;
    font-size: 14px;
    color: var(--muted);
  }
  .nav-links a{ text-decoration: none; transition: color .2s ease; }
  .nav-links a:hover{ color: var(--text); }

  /* ---------- HERO ---------- */
  .hero{
    display: grid;
    grid-template-columns: 1.25fr 1fr;
    gap: 56px;
    align-items: center;
    padding: 56px 0 88px;
    border-bottom: 1px solid var(--line);
  }
  .hero h1{
    font-size: clamp(40px, 6vw, 64px);
    line-height: 1.05;
    font-weight: 600;
    margin: 0 0 20px;
    letter-spacing: -0.01em;
  }
  .hero .role{
    font-size: 17px;
    color: var(--muted);
    max-width: 40ch;
    line-height: 1.6;
    margin: 0 0 32px;
  }
  .hero .role strong{ color: var(--text); font-weight: 500; }

  .hero-actions{
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
  }
  .btn{
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    padding: 12px 18px;
    border-radius: 3px;
    text-decoration: none;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    border: 1px solid var(--line);
    transition: border-color .2s ease, transform .15s ease;
  }
  .btn:hover{ transform: translateY(-1px); }
  .btn.primary{
    background: var(--gold);
    color: #14131c;
    border-color: var(--gold);
    font-weight: 600;
  }
  .btn.primary:hover{ background: #edb455; }
  .btn.ghost{ color: var(--text); }
  .btn.ghost:hover{ border-color: var(--gold); }

  /* Terminal card */
  .terminal{
    background: var(--panel);
    border: 1px solid var(--line);
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 30px 60px -30px rgba(0,0,0,0.6);
  }
  .terminal-bar{
    display: flex;
    align-items: center;
    gap: 7px;
    padding: 12px 14px;
    background: var(--panel-2);
    border-bottom: 1px solid var(--line);
  }
  .terminal-bar span{
    width: 9px; height: 9px; border-radius: 50%;
    background: #3a3a4f;
  }
  .terminal-bar .path{
    margin-left: 8px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--muted);
  }
  .terminal-body{
    padding: 22px 20px 26px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    line-height: 1.9;
    color: #c9c5da;
    min-height: 200px;
  }
  .terminal-body .prompt{ color: var(--gold); }
  .terminal-body .out{ color: var(--muted); }
  .terminal-body .accent{ color: var(--pink); }
  .caret{
    display: inline-block;
    width: 7px; height: 14px;
    background: var(--gold);
    margin-left: 2px;
    vertical-align: -2px;
    animation: blink 1s steps(1) infinite;
  }
  @keyframes blink{ 50%{ opacity: 0; } }

  .typeline{ opacity: 0; }
  .typeline.show{ opacity: 1; }

  /* ---------- SECTION LABELS ---------- */
  .section{ padding: 72px 0; border-bottom: 1px solid var(--line); }
  .section:last-of-type{ border-bottom: none; }
  .section-head{
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    margin-bottom: 36px;
    gap: 24px;
  }
  .section-head h2{
    font-size: 26px;
    font-weight: 600;
    margin: 0;
  }
  .section-head .idx{
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
  }

  /* ---------- ABOUT ---------- */
  .about-grid{
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 48px;
  }
  .about-grid p{
    font-size: 16px;
    line-height: 1.8;
    color: #c9c5da;
    margin: 0 0 16px;
  }
  .facts{
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--muted);
    border-left: 2px solid var(--line);
    padding-left: 20px;
  }
  .facts div{ display: flex; justify-content: space-between; padding: 9px 0; border-bottom: 1px dashed var(--line); gap: 16px; }
  .facts div:last-child{ border-bottom: none; }
  .facts span:last-child{ color: var(--text); text-align: right; }

  /* ---------- SKILLS ---------- */
  .skills{
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }
  .skill{
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    padding: 9px 14px;
    border: 1px solid var(--line);
    border-radius: 3px;
    color: #c9c5da;
    background: var(--panel);
  }
  .skill em{ color: var(--gold); font-style: normal; margin-right: 8px; }

  /* ---------- STATS ---------- */
  .stats{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1px;
    background: var(--line);
    border: 1px solid var(--line);
    border-radius: 8px;
    overflow: hidden;
  }
  .stat{
    background: var(--panel);
    padding: 30px 24px;
  }
  .stat .num{
    font-size: 40px;
    font-weight: 700;
    color: var(--gold);
    line-height: 1;
  }
  .stat .num.pink{ color: var(--pink); }
  .stat .label{
    margin-top: 10px;
    font-size: 13px;
    color: var(--muted);
  }
  .stat .sub{
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: #59566b;
    margin-top: 4px;
  }

  /* ---------- CONNECT ---------- */
  .connect-list{ display: flex; flex-direction: column; }
  .connect-row{
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 0;
    border-bottom: 1px solid var(--line);
    text-decoration: none;
    color: var(--text);
  }
  .connect-row:first-child{ border-top: 1px solid var(--line); }
  .connect-row .left{
    display: flex;
    align-items: baseline;
    gap: 18px;
  }
  .connect-row .cmd{
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: var(--muted);
    width: 90px;
    flex-shrink: 0;
  }
  .connect-row .name{ font-size: 18px; font-weight: 500; }
  .connect-row .handle{
    font-family: 'JetBrains Mono', monospace;
    font-size: 13px;
    color: var(--muted);
  }
  .connect-row .arrow{
    font-family: 'JetBrains Mono', monospace;
    color: var(--muted);
    transition: transform .2s ease, color .2s ease;
  }
  .connect-row:hover .arrow{ transform: translateX(4px); color: var(--gold); }
  .connect-row:hover .name{ color: var(--gold); }

  footer{
    padding: 40px 0 56px;
    display: flex;
    justify-content: space-between;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    color: #59566b;
  }

  @media (max-width: 760px){
    .wrap{ padding: 0 20px; }
    .hero{ grid-template-columns: 1fr; padding-top: 32px; }
    .about-grid{ grid-template-columns: 1fr; }
    .stats{ grid-template-columns: 1fr; }
    .nav-links{ display: none; }
    .connect-row .cmd{ display: none; }
  }

  :focus-visible{
    outline: 2px solid var(--gold);
    outline-offset: 3px;
  }
</style>
</head>
<body>

<div class="wrap">
  <nav class="nav">
    <div class="mark"><b>DAT</b>/dev</div>
    <div class="nav-links">
      <a href="#about">About</a>
      <a href="#skills">Skills</a>
      <a href="#activity">Activity</a>
      <a href="#connect">Connect</a>
    </div>
  </nav>

  <section class="hero">
    <div>
      <h1>Đinh Tấn Đạt</h1>
      <p class="role">Sinh viên &amp; lập trình viên tại Cần Thơ — xây dựng những công cụ nhỏ, gọn, và <strong>dùng được thật</strong>. Đang làm việc chủ yếu với JavaScript, Java và Python.</p>
      <div class="hero-actions">
        <a class="btn primary" href="mailto:dtdata24042@cusc.ctu.edu.vn">Gửi email</a>
        <a class="btn ghost" href="https://github.com/MEGAPLASTOR" target="_blank" rel="noopener">GitHub ↗</a>
      </div>
    </div>

    <div class="terminal">
      <div class="terminal-bar">
        <span></span><span></span><span></span>
        <div class="path">~/dat — zsh</div>
      </div>
      <div class="terminal-body" id="term"></div>
    </div>
  </section>

  <section class="section" id="about">
    <div class="section-head">
      <h2>Về mình</h2>
      <div class="idx">01</div>
    </div>
    <div class="about-grid">
      <div>
        <p>Mình là Đạt, hiện đang học tại Trường Công nghệ Thông tin &amp; Truyền thông, Đại học Cần Thơ. Mình thích viết code gọn gàng, thử nghiệm API, và thỉnh thoảng làm vài dự án nhỏ chỉ vì tò mò nó hoạt động thế nào.</p>
        <p>Ngoài giờ code, mình làm nội dung trên YouTube và hay lảng vảng trên Discord nhiều hơn là mạng xã hội khác.</p>
      </div>
      <div class="facts">
        <div><span>Vị trí</span><span>Cần Thơ, Việt Nam</span></div>
        <div><span>Trường</span><span>ĐH Cần Thơ (CUSC)</span></div>
        <div><span>Bắt đầu code</span><span>2021</span></div>
        <div><span>Ngôn ngữ chính</span><span>JavaScript, Java</span></div>
        <div><span>Trạng thái</span><span>Đang học &amp; xây dự án</span></div>
      </div>
    </div>
  </section>

  <section class="section" id="skills">
    <div class="section-head">
      <h2>Kỹ năng</h2>
      <div class="idx">02</div>
    </div>
    <div class="skills">
      <div class="skill"><em>&gt;</em>JavaScript</div>
      <div class="skill"><em>&gt;</em>Java</div>
      <div class="skill"><em>&gt;</em>Python</div>
      <div class="skill"><em>&gt;</em>PHP</div>
      <div class="skill"><em>&gt;</em>HTML / CSS / SCSS</div>
      <div class="skill"><em>&gt;</em>Git &amp; GitHub</div>
    </div>
  </section>

  <section class="section" id="activity">
    <div class="section-head">
      <h2>Hoạt động</h2>
      <div class="idx">03</div>
    </div>
    <div class="stats">
      <div class="stat">
        <div class="num">344</div>
        <div class="label">Tổng đóng góp</div>
        <div class="sub">Mar 2021 — Present</div>
      </div>
      <div class="stat">
        <div class="num pink">2</div>
        <div class="label">Chuỗi hiện tại</div>
        <div class="sub">Sep 4 — Sep 5</div>
      </div>
      <div class="stat">
        <div class="num">8</div>
        <div class="label">Chuỗi dài nhất</div>
        <div class="sub">Jun 25 — Jul 2</div>
      </div>
    </div>
  </section>

  <section class="section" id="connect">
    <div class="section-head">
      <h2>Kết nối</h2>
      <div class="idx">04</div>
    </div>
    <div class="connect-list">
      <a class="connect-row" href="https://github.com/MEGAPLASTOR" target="_blank" rel="noopener">
        <div class="left"><span class="cmd">open</span><span class="name">GitHub</span></div>
        <span class="handle">@MEGAPLASTOR</span>
        <span class="arrow">→</span>
      </a>
      <a class="connect-row" href="https://www.facebook.com/MEGAPLASTORR/?locale=vi_VN" target="_blank" rel="noopener">
        <div class="left"><span class="cmd">open</span><span class="name">Facebook</span></div>
        <span class="handle">MEGAPLASTORR</span>
        <span class="arrow">→</span>
      </a>
      <a class="connect-row" href="https://www.youtube.com/@Veloriablox" target="_blank" rel="noopener">
        <div class="left"><span class="cmd">open</span><span class="name">YouTube</span></div>
        <span class="handle">@Veloriablox</span>
        <span class="arrow">→</span>
      </a>
      <div class="connect-row" style="cursor:default;">
        <div class="left"><span class="cmd">msg</span><span class="name">Discord</span></div>
        <span class="handle">megaplastorr</span>
        <span class="arrow"> </span>
      </div>
      <a class="connect-row" href="mailto:dtdata24042@cusc.ctu.edu.vn">
        <div class="left"><span class="cmd">mail</span><span class="name">Email</span></div>
        <span class="handle">dtdata24042@cusc.ctu.edu.vn</span>
        <span class="arrow">→</span>
      </a>
    </div>
  </section>

  <footer>
    <span>© 2026 Đinh Tấn Đạt</span>
    <span>built with care, not a template</span>
  </footer>
</div>

<script>
  const lines = [
    { p: '$ whoami', d: 0 },
    { o: 'dinh_tan_dat — student, developer', d: 0 },
    { p: '$ cat focus.txt', d: 0 },
    { a: 'building small, useful things.', d: 0 },
    { p: '$ status --current', d: 0 },
    { o: 'available for collab & ideas', d: 0 },
  ];

  const term = document.getElementById('term');
  let html = '';
  lines.forEach((l, i) => {
    const cls = l.p ? 'prompt' : (l.a ? 'accent' : 'out');
    const text = l.p || l.a || l.o;
    html += `<div class="typeline" style="transition-delay:${i * 220}ms"><span class="${cls}">${text}</span></div>`;
  });
  html += `<div class="typeline" style="transition-delay:${lines.length * 220}ms"><span class="prompt">$</span><span class="caret"></span></div>`;
  term.innerHTML = html;

  requestAnimationFrame(() => {
    setTimeout(() => {
      document.querySelectorAll('.typeline').forEach(el => el.classList.add('show'));
    }, 50);
  });
</script>

</body>
</html>

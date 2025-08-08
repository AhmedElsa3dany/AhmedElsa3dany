<!doctype html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Ahmed Elsaadany — Profile</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&family=Almarai:wght@300;400;700&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg1: #0f172a;
      --card: linear-gradient(135deg,#0ea5e9, #8b5cf6);
      --accent1: #06b6d4;
      --accent2: #a78bfa;
      --glass: rgba(255,255,255,0.04);
      --text: #e6eef8;
      --muted: #9fb3cf;
      --success: #34d399;
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: "Almarai", "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: radial-gradient(1200px 600px at 10% 10%, rgba(167,139,250,0.08), transparent),
                  radial-gradient(700px 400px at 90% 90%, rgba(6,182,212,0.06), transparent),
                  var(--bg1);
      color:var(--text);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      min-height:100vh;
      padding:40px 20px;
    }

    .container{
      max-width:1000px;
      margin:0 auto;
      display:grid;
      grid-template-columns: 320px 1fr;
      gap:24px;
      align-items:start;
    }

    /* profile card */
    .card{
      background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
      border-radius:16px;
      padding:22px;
      box-shadow: 0 6px 30px rgba(2,6,23,0.6);
      position:relative;
      overflow:hidden;
      border:1px solid rgba(255,255,255,0.04);
    }

    /* animated accent blob */
    .accent-blob{
      position:absolute;
      width:220px; height:220px;
      right:-60px; top:-60px;
      background: radial-gradient(circle at 30% 30%, rgba(167,139,250,0.25), transparent 40%),
                  radial-gradient(circle at 70% 70%, rgba(6,182,212,0.15), transparent 40%);
      filter: blur(30px);
      transform: rotate(10deg);
      pointer-events:none;
      animation: blob 8s infinite;
    }
    @keyframes blob{
      0%{transform: translateY(0) rotate(0deg) scale(1)}
      50%{transform: translateY(-12px) rotate(6deg) scale(1.05)}
      100%{transform: translateY(0) rotate(0deg) scale(1)}
    }

    .avatar{
      width:96px; height:96px;
      border-radius:14px;
      background: linear-gradient(135deg,var(--accent1), var(--accent2));
      display:flex;
      align-items:center;
      justify-content:center;
      font-weight:800;
      font-size:28px;
      color:white;
      margin-left:10px;
      box-shadow: 0 6px 18px rgba(0,0,0,0.45);
    }

    h1{margin:0; font-size:20px}
    h2{margin:6px 0 0; font-size:13px; color:var(--muted)}
    .contact{margin-top:12px; font-size:13px; color:var(--muted); line-height:1.6}
    .links a{display:inline-block; margin-left:6px; font-weight:600; color:var(--text); text-decoration:none}
    .pill{display:inline-block; padding:6px 10px; background:var(--glass); border-radius:999px; font-size:12px; color:var(--muted); margin:6px 6px 0 0}

    /* main content */
    .main{
      display:flex;
      flex-direction:column;
      gap:18px;
    }

    .section-title{
      display:flex; align-items:center; gap:10px;
      font-weight:700; color:var(--accent2);
      margin-bottom:8px;
    }

    .summary{
      font-size:14px; color:var(--text); line-height:1.6;
      background: linear-gradient(90deg, rgba(255,255,255,0.01), rgba(255,255,255,0.015));
      padding:12px; border-radius:12px; border:1px solid rgba(255,255,255,0.03);
    }

    .projects{display:grid; grid-template-columns:1fr 1fr; gap:12px}
    .proj{
      background: linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      padding:12px; border-radius:12px; border:1px solid rgba(255,255,255,0.03);
      transform:translateY(8px); opacity:0; animation: cardIn 800ms forwards;
    }
    .proj:nth-child(1){animation-delay:120ms}
    .proj:nth-child(2){animation-delay:220ms}
    .proj:nth-child(3){animation-delay:320ms}
    .proj:nth-child(4){animation-delay:420ms}

    @keyframes cardIn{
      to{transform:none; opacity:1}
    }

    .meta{font-size:12px; color:var(--muted); margin-top:8px}

    .skills{display:flex; gap:12px; flex-wrap:wrap}
    .skill{
      width:100%; display:block;
      background:rgba(255,255,255,0.02); padding:10px; border-radius:10px;
      border:1px solid rgba(255,255,255,0.03);
    }
    .skill .bar{
      height:10px; border-radius:999px; overflow:hidden; background:rgba(255,255,255,0.03); margin-top:8px;
    }
    .skill .bar > i{
      display:block; height:100%; width:0%; background:linear-gradient(90deg,var(--accent1),var(--accent2));
      border-radius:999px; animation: fillBar 1.6s ease forwards;
    }
    @keyframes fillBar{
      to{width: var(--pct)}
    }

    .footer{
      display:flex; justify-content:space-between; gap:12px; align-items:center; margin-top:6px; color:var(--muted);
      font-size:13px;
    }

    /* particles canvas */
    #particles{
      position:fixed; left:0; top:0; width:100%; height:100%; z-index:0; pointer-events:none;
      mix-blend-mode: screen;
    }

    /* responsive */
    @media (max-width:880px){
      .container{grid-template-columns:1fr; padding-bottom:40px}
      .projects{grid-template-columns:1fr}
    }

  </style>
</head>
<body>
  <canvas id="particles"></canvas>

  <div class="container" style="position:relative; z-index:1;">
    <!-- LEFT: profile -->
    <div class="card" aria-label="بطاقة الملف الشخصي">
      <div class="accent-blob" aria-hidden="true"></div>

      <div style="display:flex; align-items:center; gap:12px;">
        <div class="avatar" title="أحمد السعداني">AS</div>
        <div>
          <h1>أحمد السعداني</h1>
          <h2>طالب علوم الحاسب | مطوّر تطبيقات موبايل</h2>
          <div class="pill">New Mansoura University</div>
          <div class="pill">GPA: 3.6 / 4.0</div>
        </div>
      </div>

      <div class="contact" style="margin-top:14px;">
        <div>📍 مصر، القاهرة</div>
        <div>✉️ <a href="mailto:ahmedelsaadany16112003@gmail.com" style="color:var(--text)">ahmedelsaadany16112003@gmail.com</a></div>
        <div>📞 +20 1016922983</div>

        <div style="margin-top:10px;" class="links">
          <a href="https://github.com/AhmedElsa3dany" target="_blank">GitHub</a> |
          <a href="https://www.linkedin.com/in/ahmed-elsa3dany/" target="_blank">LinkedIn</a>
        </div>
      </div>

      <div style="margin-top:16px;">
        <div class="section-title">الخبرات & الدورات</div>
        <div style="display:flex;flex-direction:column;gap:8px;margin-top:8px;">
          <div class="meta">• متدرب تطوير تطبيقات موبايل — ByteUprise (Aug–Oct 2024)</div>
          <div class="meta">• Huawei Campus Ambassador — منذ Dec 2024</div>
          <div class="meta">• دورات: Flutter & Dart, DSA, Bloc & MVVM، Git & GitHub.</div>
        </div>
      </div>

      <div style="margin-top:16px;">
        <div class="section-title">التطوع</div>
        <div class="meta">• نائب رئيس Rally New Mansoura (Nov 2024 – Present)</div>
        <div class="meta">• Head of Operations — Microsoft Student Club</div>
      </div>

      <div class="footer">
        <div style="font-size:12px">متاح للعمل الحر وورش العمل</div>
        <div style="font-size:12px">👨‍💻 Flutter • AI • Computer Vision</div>
      </div>
    </div>

    <!-- RIGHT: main content -->
    <div class="main">
      <div class="card">
        <div class="section-title">ملخص احترافي</div>
        <div class="summary">
          مبرمج ومطوّر تطبيقات موبايل (Flutter & Dart) وطالب بكالوريوس هندسة برمجيات. خبرة في بناء تطبيقات تعليمية ومساعدة تستخدم AI و3D، وقائد مشاريع فائزة مثل <strong>Kidventure</strong> و<strong>SMILe</strong> (فازتا بالمركز الأول في مسابقات محلية). أحب تصميم واجهات مستخدم جذابة وبناء حلول تعليمية واجتماعية. :contentReference[oaicite:1]{index=1}
        </div>
      </div>

      <div class="card">
        <div class="section-title">أهم المشاريع</div>

        <div class="projects" style="margin-top:8px;">
          <div class="proj">
            <strong>SMILe App</strong> — تطبيق مساعد للأطفال ذوي طيف التوحد (AI, Firebase, Flutter). فاز بالمركز الأول — Benha Hackathon. 
            <div class="meta">ميزات: emotion recognition، gamification، voice/symbol communication. :contentReference[oaicite:2]{index=2}</div>
          </div>

          <div class="proj">
            <strong>Kidventure</strong> — تطبيق تعليمي للأطفال مع 3D وchatbot وflashcards. فاز بالمركز الأول — Creativa Marathon. 
            <div class="meta">ميزات: 3D models, chatbot, tracking, gamified quizzes. :contentReference[oaicite:3]{index=3}</div>
          </div>

          <div class="proj">
            <strong>BookNest</strong> — تطبيق قراءة متكامل مع MVVM & BLoC، Dio للـ APIs (مشروع شخصي).</div>

          <div class="proj">
            <strong>Responsive Dashboard</strong> — واجهة متجاوبة للهاتف والتابلت والويب (مشروع شخصي، مستمر).</div>
        </div>
      </div>

      <div class="card">
        <div class="section-title">المهارات</div>

        <div style="margin-top:10px;" class="skills">
          <div class="skill">
            <div style="display:flex;justify-content:space-between"><strong>Flutter & Dart</strong><small>90%</small></div>
            <div class="bar" style="--pct:90%"><i></i></div>
          </div>

          <div class="skill">
            <div style="display:flex;justify-content:space-between"><strong>Firebase / Backend</strong><small>75%</small></div>
            <div class="bar" style="--pct:75%"><i></i></div>
          </div>

          <div class="skill">
            <div style="display:flex;justify-content:space-between"><strong>AI / Prompt Engineering</strong><small>70%</small></div>
            <div class="bar" style="--pct:70%"><i></i></div>
          </div>

          <div class="skill">
            <div style="display:flex;justify-content:space-between"><strong>Clean Architecture & State Mgmt</strong><small>80%</small></div>
            <div class="bar" style="--pct:80%"><i></i></div>
          </div>
        </div>
      </div>

      <div class="card">
        <div class="section-title">التعليم والدورات</div>
        <div class="meta">New Mansoura University — Bachelor of Software Engineering (متوقع 2026). GPA 3.6/4.0. :contentReference[oaicite:4]{index=4}</div>
        <ul style="margin-top:10px; color:var(--muted); line-height:1.7">
          <li>Mastering Flutter & Dart (دورات عربية)</li>
          <li>Flutter Advanced: Bloc & MVVM</li>
          <li>Mastering Programming: DSA (Arabic)</li>
        </ul>
      </div>

      <div class="card">
        <div class="section-title">التواصل</div>
        <div style="display:flex;gap:12px;flex-wrap:wrap; align-items:center;">
          <a href="https://github.com/AhmedElsa3dany" target="_blank" class="pill">GitHub</a>
          <a href="https://www.linkedin.com/in/ahmed-elsa3dany/" target="_blank" class="pill">LinkedIn</a>
          <a href="mailto:ahmedelsaadany16112003@gmail.com" class="pill">Email</a>
          <a href="tel:+201016922983" class="pill">Phone</a>
        </div>

        <div style="margin-top:12px; color:var(--muted); font-size:13px">
          للمشاريع أو التعاون تواصل معي — أحب العمل على حلول تعليمية وواجهات مستخدم جذابة.
        </div>
      </div>
    </div>
  </div>

  <script>
    /* simple particles background */
    const canvas = document.getElementById('particles');
    const ctx = canvas.getContext('2d');
    let w = canvas.width = innerWidth;
    let h = canvas.height = innerHeight;
    const pts = [];
    for(let i=0;i<60;i++){
      pts.push({x:Math.random()*w, y:Math.random()*h, r: Math.random()*1.6+0.3, vx:(Math.random()-0.5)/2, vy:(Math.random()-0.5)/2});
    }
    function resize(){ w=canvas.width=innerWidth; h=canvas.height=innerHeight; }
    addEventListener('resize', resize);
    function frame(){
      ctx.clearRect(0,0,w,h);
      for(let p of pts){
        p.x += p.vx; p.y += p.vy;
        if(p.x<0) p.x=w; if(p.x>w) p.x=0;
        if(p.y<0) p.y=h; if(p.y>h) p.y=0;
        ctx.beginPath();
        ctx.fillStyle = 'rgba(167,139,250,0.06)';
        ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
        ctx.fill();
      }
      requestAnimationFrame(frame);
    }
    frame();

    /* typing effect for the summary (optional extension) */
    // (kept simple — the visible summary is static; you can enable dynamic typing if needed)

    /* animate skill bars on load */
    window.addEventListener('load', ()=>{
      document.querySelectorAll('.skill .bar > i').forEach((el, idx)=>{
        // trigger animation by forcing reflow (already defined in CSS)
        const pct = getComputedStyle(el.parentElement).getPropertyValue('--pct') || '70%';
        el.style.width = pct;
      });
    });
  </script>
</body>
</html>

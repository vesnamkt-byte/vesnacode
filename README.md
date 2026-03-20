[index (2).html](https://github.com/user-attachments/files/26130848/index.2.html){
  "rewrites": [
    { "source": "/brands/:brand", "destination": "/brands/:brand/index.html" }
  ],
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        { "key": "Cache-Control", "value": "public, max-age=3600" }
      ]
    }
  ]
}

[vercel.json](https://github.com/user-attachments/files/26130847/vercel.json)
[Uploading<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>DualMac · Pitch Decks</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="shared/css/base.css" />

  <style>
    :root {
      --bg: #070B14;
      --bg-2: #0D1220;
      --bg-3: #111827;
      --border: rgba(0,229,204,0.1);
      --border-hover: rgba(0,229,204,0.35);
      --text: #EBF4F7;
      --text-muted: rgba(190,220,230,0.5);
      --accent: #00E5CC;
      --accent-2: #7C6DFA;
      --accent-3: #F0A500;
      --font-display: 'Syne', sans-serif;
      --font-body: 'DM Sans', sans-serif;
    }

    body {
      min-height: 100vh;
      background: var(--bg);
      background-image:
        linear-gradient(rgba(0,229,204,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,229,204,0.025) 1px, transparent 1px);
      background-size: 60px 60px;
      display: flex;
      flex-direction: column;
    }

    header {
      padding: 2rem var(--sp-md);
      border-bottom: 1px solid var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .logo {
      font-family: var(--font-display);
      font-size: 1.25rem;
      font-weight: 800;
      letter-spacing: -0.02em;
      color: var(--text);
    }
    .logo span { color: var(--accent); }

    main {
      flex: 1;
      padding: var(--sp-xl) var(--sp-md);
      max-width: var(--max-w);
      margin: 0 auto;
      width: 100%;
    }

    .page-title {
      font-family: var(--font-display);
      font-size: clamp(2.5rem, 6vw, 5rem);
      font-weight: 800;
      letter-spacing: -0.03em;
      line-height: 1.0;
      margin-bottom: 1rem;
    }

    .brand-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 1.5rem;
      margin-top: 3rem;
    }

    .brand-card {
      display: block;
      background: var(--bg-2);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 2rem;
      text-decoration: none;
      color: var(--text);
      transition: border-color 0.4s, transform 0.4s cubic-bezier(0.16,1,0.3,1), box-shadow 0.4s;
      position: relative;
      overflow: hidden;
    }
    .brand-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(ellipse at 0% 0%, var(--card-glow), transparent 60%);
      opacity: 0;
      transition: opacity 0.4s;
    }
    .brand-card:hover {
      border-color: var(--border-hover);
      transform: translateY(-6px);
      box-shadow: 0 20px 60px rgba(0,0,0,0.4);
    }
    .brand-card:hover::before { opacity: 1; }

    .brand-card__tag {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--card-color, var(--accent));
      margin-bottom: 1rem;
      display: flex;
      align-items: center;
      gap: 0.4rem;
    }
    .brand-card__tag::before {
      content: '';
      width: 16px; height: 1px;
      background: currentColor;
    }

    .brand-card__name {
      font-family: var(--font-display);
      font-size: 1.5rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
      line-height: 1.2;
    }

    .brand-card__desc {
      font-size: var(--fs-sm);
      color: var(--text-muted);
      line-height: 1.6;
      margin-bottom: 1.5rem;
    }

    .brand-card__meta {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-top: 1px solid var(--border);
      padding-top: 1rem;
      font-size: 0.7rem;
      color: var(--text-muted);
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }

    .brand-card__arrow {
      width: 32px; height: 32px;
      border: 1px solid var(--border);
      border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-size: 0.75rem;
      transition: border-color 0.3s, background 0.3s;
      color: var(--card-color, var(--accent));
    }
    .brand-card:hover .brand-card__arrow {
      background: var(--card-color, var(--accent));
      color: var(--bg);
      border-color: transparent;
    }

    .add-card {
      border: 1px dashed var(--border);
      border-radius: var(--radius-lg);
      padding: 2rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 200px;
      gap: 0.75rem;
      color: var(--text-muted);
      font-size: var(--fs-sm);
      cursor: default;
    }
    .add-card__icon {
      width: 40px; height: 40px;
      border: 1px dashed var(--border-hover);
      border-radius: 50%;
      display: flex; align-items:center; justify-content:center;
      font-size: 1.2rem;
      color: var(--border-hover);
    }

    footer {
      padding: 2rem var(--sp-md);
      border-top: 1px solid var(--border);
      text-align: center;
      font-size: var(--fs-xs);
      color: var(--text-muted);
      letter-spacing: 0.06em;
    }

    @media (max-width: 600px) {
      .brand-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body class="noise">
  <div id="progress-bar"></div>

  <header>
    <div class="logo">Dual<span>Mac</span></div>
    <span style="font-size:var(--fs-xs);color:var(--text-muted);letter-spacing:0.1em;text-transform:uppercase;">Propuestas · 2025</span>
  </header>

  <main>
    <div>
      <p style="font-size:var(--fs-xs);font-weight:700;letter-spacing:0.15em;text-transform:uppercase;color:var(--accent);margin-bottom:0.75rem;display:flex;align-items:center;gap:0.5rem;">
        <span style="display:inline-block;width:24px;height:1px;background:var(--accent);"></span>
        Pitch Decks Interactivos
      </p>
      <h1 class="page-title">
        Propuestas<br/>
        <span style="color:var(--accent);">estratégicas.</span>
      </h1>
      <p style="font-size:var(--fs-lg);color:var(--text-muted);max-width:560px;line-height:1.7;margin-top:1rem;">
        Cada marca, una estrategia diseñada para convertir valor real en resultados digitales.
      </p>
    </div>

    <div class="brand-grid">

      <!-- Buena Salud -->
      <a href="./brands/buena-salud/index.html" class="brand-card"
         style="--card-color:#00E5CC; --card-glow:rgba(0,229,204,0.08);">
        <div class="brand-card__tag">Salud · Neurorrehabilitación</div>
        <div class="brand-card__name">Clínica Hogar<br/>Buena Salud</div>
        <div class="brand-card__desc">
          Estrategia digital completa para clínica de neurorrehabilitación. Plan Black · 36 piezas mensuales.
        </div>
        <div class="brand-card__meta">
          <span>Plan Black · $2.189.981 CLP/mes</span>
          <div class="brand-card__arrow">→</div>
        </div>
      </a>

      <!-- Placeholder for future brands -->
      <div class="add-card">
        <div class="add-card__icon">+</div>
        <span>Próxima marca</span>
        <span style="font-size:var(--fs-xs)">Agrega /brands/nueva-marca/</span>
      </div>

      <div class="add-card">
        <div class="add-card__icon">+</div>
        <span>Próxima marca</span>
        <span style="font-size:var(--fs-xs)">Agrega /brands/nueva-marca/</span>
      </div>

    </div>
  </main>

  <footer>
    DualMac · Sistema de Pitch Decks Interactivos · 2025
  </footer>

  <script>
    // Simple progress bar for landing
    const bar = document.getElementById('progress-bar');
    window.addEventListener('scroll', () => {
      const p = window.scrollY / (document.documentElement.scrollHeight - window.innerHeight) * 100;
      bar.style.width = p + '%';
    }, { passive: true });
  </script>
</body>
</html>
 index (2).html…]()
[buena-salud.json](https://github.com/user-attachments/files/26130849/buena-salud.json)
{
  "brand": "Clínica Hogar Buena Salud",
  "tagline": "Donde la recuperación se convierte en un proceso real.",
  "agency": "DualMac",
  "plan": "Plan Black",
  "price": "$2.189.981 CLP",
  "priceLabel": "mensuales",
  "kpis": [
    { "value": 36, "suffix": "", "label": "Piezas de contenido mensual", "icon": "✦" },
    { "value": 116, "suffix": "%", "label": "Más presencia digital", "icon": "↑" },
    { "value": 2000, "suffix": "+", "label": "Seguidores mensuales", "icon": "◎" },
    { "value": 3, "suffix": "+", "label": "Reuniones estratégicas al mes", "icon": "◈" }
  ],
  "contenido": [
    { "qty": 12, "tipo": "Posts Mensuales", "desc": "Cápsulas estratégicas: equipo médico, tecnología, historias de pacientes, educación y proceso clínico." },
    { "qty": 16, "tipo": "Historias Mensuales", "desc": "Presencia constante, cercanía con la audiencia y refuerzo de marca diario." },
    { "qty": 8, "tipo": "Reels Mensuales", "desc": "Formato clave para crecimiento. 4 reels opcionales con IA: avatares, UGC, edición avanzada." }
  ],
  "pilares": [
    {
      "rol": "HÉROE",
      "nombre": "El Paciente",
      "desc": "Vive el proceso de transformación. Pasa de una situación crítica a recuperar funciones clave de su vida.",
      "color": "#00E5CC"
    },
    {
      "rol": "CUIDADOR",
      "nombre": "La Clínica",
      "desc": "Acompaña, contiene y guía. Trabajo interdisciplinario con presencia constante de fisiatra y participación activa de la familia.",
      "color": "#A78BFA"
    },
    {
      "rol": "SABIO",
      "nombre": "El Equipo",
      "desc": "Entrega seguridad, conocimiento y dirección. Profesionales especializados con tecnología avanzada TrainFES.",
      "color": "#F59E0B"
    }
  ],
  "nichos": [
    { "nombre": "Pacientes y Familias", "desc": "Personas post-ACV o con daño neurológico. Familiares que toman decisiones buscando soluciones confiables y rápidas.", "tag": "B2C" },
    { "nombre": "Médicos Derivadores", "desc": "Neurólogos, traumatólogos y médicos tratantes. Influyen directamente en la decisión de internación.", "tag": "B2B" },
    { "nombre": "Entorno Académico", "desc": "Internos, universidades y redes profesionales. Posicionamiento a largo plazo.", "tag": "B2B+" }
  ],
  "servicios": [
    { "nombre": "Construcción de Marca", "icon": "◆" },
    { "nombre": "Estrategia de Contenido", "icon": "◇" },
    { "nombre": "Campañas Meta Ads", "icon": "▲" },
    { "nombre": "Optimización del Ecosistema", "icon": "○" },
    { "nombre": "Tecnología + IA", "icon": "✦" },
    { "nombre": "Monitoreo y Reportes", "icon": "◉" }
  ],
  "chartLabels": ["Mes 1", "Mes 2", "Mes 3", "Mes 4", "Mes 5", "Mes 6"],
  "chartSeguimientoOrganico": [800, 1600, 2900, 4500, 6200, 8000],
  "chartAlcancePagado": [2000, 5000, 9000, 14000, 20000, 28000]
}
[core.js](https://github.com/user-attachments/files/26130850/core.js)
/* =============================================
   SHARED CORE JS — pitch-deck platform
   ============================================= */

/* ---------- Progress Bar ---------- */
function initProgressBar() {
  const bar = document.getElementById('progress-bar');
  if (!bar) return;
  window.addEventListener('scroll', () => {
    const scrollTop = window.scrollY;
    const docHeight = document.documentElement.scrollHeight - window.innerHeight;
    bar.style.width = (scrollTop / docHeight * 100) + '%';
  }, { passive: true });
}

/* ---------- Animated Counter ---------- */
function animateCounter(el) {
  const target = parseFloat(el.dataset.target) || 0;
  const suffix = el.dataset.suffix || '';
  const duration = 2.0;
  gsap.fromTo(
    el,
    { innerText: 0 },
    {
      innerText: target,
      duration,
      ease: 'power3.out',
      snap: { innerText: target > 100 ? 50 : 1 },
      onUpdate() {
        const v = Math.round(parseFloat(this.targets()[0].innerText));
        this.targets()[0].innerText = v.toLocaleString('es-CL') + suffix;
      },
      onComplete() {
        el.innerText = target.toLocaleString('es-CL') + suffix;
      }
    }
  );
}

function initCounters() {
  const els = document.querySelectorAll('[data-counter]');
  if (!els.length) return;

  els.forEach(el => {
    ScrollTrigger.create({
      trigger: el,
      start: 'top 85%',
      once: true,
      onEnter: () => animateCounter(el)
    });
  });
}

/* ---------- Video Autoplay on viewport ---------- */
function initVideoAutoplay() {
  const videos = document.querySelectorAll('.phone__screen video, [data-autoplay]');
  if (!videos.length) return;

  const obs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.play().catch(() => {});
      } else {
        e.target.pause();
      }
    });
  }, { threshold: 0.3 });

  videos.forEach(v => {
    v.muted = true;
    v.loop = true;
    v.playsInline = true;
    obs.observe(v);
  });
}

/* ---------- Hover video cards ---------- */
function initHoverVideos() {
  document.querySelectorAll('[data-hover-video]').forEach(card => {
    const video = card.querySelector('video');
    if (!video) return;
    video.muted = true; video.loop = true; video.playsInline = true;
    card.addEventListener('mouseenter', () => video.play().catch(() => {}));
    card.addEventListener('mouseleave', () => { video.pause(); video.currentTime = 0; });
  });
}

/* ---------- Nav Dots ---------- */
function initNavDots(sections) {
  const container = document.getElementById('nav-dots');
  if (!container || !sections.length) return;

  sections.forEach((sec, i) => {
    const dot = document.createElement('button');
    dot.className = 'nav-dot';
    dot.setAttribute('aria-label', `Ir a sección ${i + 1}`);
    dot.addEventListener('click', () => sec.scrollIntoView({ behavior: 'smooth' }));
    container.appendChild(dot);

    ScrollTrigger.create({
      trigger: sec,
      start: 'top center',
      end: 'bottom center',
      onToggle: self => {
        dot.classList.toggle('active', self.isActive);
      }
    });
  });
}

/* ---------- Reveal on scroll (non-pinned sections) ---------- */
function initReveal() {
  document.querySelectorAll('.reveal').forEach(el => {
    gsap.fromTo(el,
      { opacity: 0, y: 40 },
      {
        opacity: 1, y: 0,
        duration: 0.9,
        ease: 'power3.out',
        scrollTrigger: {
          trigger: el,
          start: 'top 85%',
          once: true
        }
      }
    );
  });
}

/* ---------- Load JSON data ---------- */
async function loadData(path) {
  try {
    const res = await fetch(path);
    return await res.json();
  } catch (e) {
    console.warn('Could not load data:', path, e);
    return null;
  }
}

/* ---------- Export ---------- */
window.PitchCore = {
  initProgressBar,
  initCounters,
  initVideoAutoplay,
  initHoverVideos,
  initNavDots,
  initReveal,
  loadData
};
[base.css](https://github.com/user-attachments/files/26130851/base.css)
/* =============================================
   SHARED BASE CSS — pitch-deck platform
   ============================================= */

/* ---------- Reset ---------- */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--font-body);
  font-size: var(--fs-base);
  line-height: 1.6;
  overflow-x: hidden;
}
img, video { max-width: 100%; display: block; }
a { color: inherit; text-decoration: none; }

/* ---------- CSS Variables (defaults — overridden by theme.css) ---------- */
:root {
  /* Colors */
  --bg:           #0A0A0F;
  --bg-2:         #111118;
  --bg-3:         #18181F;
  --border:       rgba(255,255,255,0.08);
  --border-hover: rgba(255,255,255,0.22);
  --text:         #F0EEF8;
  --text-muted:   rgba(240,238,248,0.45);
  --accent:       #00E5CC;
  --accent-2:     #A78BFA;
  --accent-3:     #F59E0B;
  --danger:       #FF4D6D;

  /* Typography */
  --font-display: 'Syne', sans-serif;
  --font-body:    'DM Sans', sans-serif;
  --fs-base:      1rem;
  --fs-sm:        0.875rem;
  --fs-xs:        0.75rem;
  --fs-lg:        1.25rem;
  --fs-xl:        1.5rem;
  --fs-2xl:       2rem;
  --fs-3xl:       clamp(2.5rem, 6vw, 4.5rem);
  --fs-4xl:       clamp(3rem, 9vw, 7rem);

  /* Spacing */
  --sp-xs:  0.5rem;
  --sp-sm:  1rem;
  --sp-md:  2rem;
  --sp-lg:  4rem;
  --sp-xl:  6rem;
  --sp-2xl: 10rem;

  /* Layout */
  --max-w: 1200px;
  --radius: 1rem;
  --radius-sm: 0.5rem;
  --radius-lg: 1.5rem;

  /* Transitions */
  --ease: cubic-bezier(0.16, 1, 0.3, 1);
  --dur: 0.6s;
}

/* ---------- Progress Bar ---------- */
#progress-bar {
  position: fixed;
  top: 0; left: 0;
  height: 2px;
  width: 0%;
  background: linear-gradient(90deg, var(--accent), var(--accent-2));
  z-index: 1000;
  transition: width 0.1s linear;
  box-shadow: 0 0 8px var(--accent);
}

/* ---------- Layout Utilities ---------- */
.container {
  width: min(var(--max-w), 100% - var(--sp-md) * 2);
  margin-inline: auto;
}

.section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding-block: var(--sp-xl);
  position: relative;
}

.section--center {
  justify-content: center;
  text-align: center;
}

/* ---------- Typography ---------- */
.display {
  font-family: var(--font-display);
  font-size: var(--fs-4xl);
  font-weight: 800;
  line-height: 1.0;
  letter-spacing: -0.03em;
}

.heading {
  font-family: var(--font-display);
  font-size: var(--fs-3xl);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
}

.label {
  font-size: var(--fs-xs);
  font-weight: 600;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--accent);
}

.muted { color: var(--text-muted); }

/* ---------- Grid Systems ---------- */
.grid-2 {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--sp-md);
}
.grid-3 {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--sp-md);
}
.grid-auto {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--sp-md);
}

@media (max-width: 768px) {
  .grid-2, .grid-3, .grid-auto { grid-template-columns: 1fr; }
}

/* ---------- Cards ---------- */
.card {
  background: var(--bg-2);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: var(--sp-md);
  transition: border-color var(--dur) var(--ease), transform 0.3s var(--ease);
}
.card:hover {
  border-color: var(--border-hover);
  transform: translateY(-4px);
}
.card--accent { border-color: var(--accent); }

/* ---------- KPI Counter ---------- */
.kpi-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: var(--sp-md);
}

.kpi-card {
  background: var(--bg-2);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: var(--sp-md) var(--sp-sm);
  text-align: center;
  position: relative;
  overflow: hidden;
  transition: border-color 0.4s;
}
.kpi-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at 50% 0%, var(--accent-glow, rgba(0,229,204,0.08)), transparent 70%);
  pointer-events: none;
}
.kpi-card:hover { border-color: var(--accent); }

.kpi-icon {
  font-size: 1.5rem;
  color: var(--accent);
  margin-bottom: var(--sp-sm);
  display: block;
}
.kpi-number {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 5vw, 4rem);
  font-weight: 800;
  line-height: 1;
  color: var(--text);
  letter-spacing: -0.03em;
}
.kpi-suffix {
  font-family: var(--font-display);
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  color: var(--accent);
  font-weight: 700;
}
.kpi-label {
  margin-top: var(--sp-xs);
  font-size: var(--fs-sm);
  color: var(--text-muted);
  line-height: 1.3;
}

/* ---------- Phone Mockup ---------- */
.phone {
  width: 220px;
  height: 440px;
  background: var(--bg-3);
  border-radius: 32px;
  border: 2px solid rgba(255,255,255,0.12);
  position: relative;
  overflow: hidden;
  box-shadow: 0 32px 64px rgba(0,0,0,0.5), inset 0 0 0 1px rgba(255,255,255,0.04);
  flex-shrink: 0;
}
.phone::before {
  content: '';
  position: absolute;
  top: 14px; left: 50%;
  transform: translateX(-50%);
  width: 80px; height: 22px;
  background: var(--bg);
  border-radius: 14px;
  z-index: 10;
}
.phone__screen {
  position: absolute;
  inset: 0;
  overflow: hidden;
  border-radius: 30px;
}
.phone__screen video,
.phone__screen img {
  width: 100%; height: 100%;
  object-fit: cover;
}
.phone__screen--ui {
  padding: 48px 12px 12px;
  background: var(--bg-3);
  display: flex;
  flex-direction: column;
  gap: 8px;
}

/* ---------- Laptop Mockup ---------- */
.laptop {
  width: 480px;
  max-width: 100%;
  position: relative;
}
.laptop__screen {
  background: var(--bg);
  border-radius: 12px 12px 0 0;
  border: 2px solid rgba(255,255,255,0.1);
  aspect-ratio: 16/10;
  overflow: hidden;
  position: relative;
}
.laptop__screen::before {
  content: '';
  position: absolute;
  top: 6px; left: 50%;
  transform: translateX(-50%);
  width: 6px; height: 6px;
  background: rgba(255,255,255,0.2);
  border-radius: 50%;
  z-index: 10;
}
.laptop__screen img,
.laptop__screen video { width: 100%; height: 100%; object-fit: cover; }
.laptop__base {
  height: 20px;
  background: linear-gradient(180deg, rgba(255,255,255,0.06), rgba(255,255,255,0.02));
  border-radius: 0 0 4px 4px;
  border: 1px solid rgba(255,255,255,0.06);
  border-top: none;
}
.laptop__stand {
  width: 120px; height: 12px;
  background: rgba(255,255,255,0.04);
  border-radius: 0 0 8px 8px;
  margin: 0 auto;
  border: 1px solid rgba(255,255,255,0.05);
  border-top: none;
}

/* ---------- Tag / Badge ---------- */
.tag {
  display: inline-flex;
  align-items: center;
  gap: 0.3em;
  padding: 0.25em 0.75em;
  border-radius: 100px;
  font-size: var(--fs-xs);
  font-weight: 600;
  letter-spacing: 0.08em;
  border: 1px solid currentColor;
}
.tag--accent { color: var(--accent); background: rgba(0,229,204,0.08); }
.tag--purple { color: var(--accent-2); background: rgba(167,139,250,0.08); }
.tag--amber  { color: var(--accent-3); background: rgba(245,158,11,0.08); }

/* ---------- Divider ---------- */
.divider {
  height: 1px;
  background: var(--border);
  margin-block: var(--sp-md);
}

/* ---------- Noise texture overlay ---------- */
.noise::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 9999;
  opacity: 0.35;
}

/* ---------- Scroll-animated elements (initial states) ---------- */
.reveal {
  opacity: 0;
  transform: translateY(40px);
}
.reveal.is-visible {
  opacity: 1;
  transform: translateY(0);
  transition: opacity 0.8s var(--ease), transform 0.8s var(--ease);
}

/* ---------- Nav dots ---------- */
#nav-dots {
  position: fixed;
  right: 1.5rem;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  z-index: 100;
}
.nav-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--border-hover);
  cursor: pointer;
  transition: background 0.3s, transform 0.3s;
}
.nav-dot.active {
  background: var(--accent);
  transform: scale(1.6);
}

@media (max-width: 768px) {
  #nav-dots { display: none; }
  .phone { width: 160px; height: 320px; }
  .laptop { width: 100%; }
}

/* ---------- Animated gradient text ---------- */
.grad-text {
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-2) 50%, var(--accent-3) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* ---------- Glow effect ---------- */
.glow {
  box-shadow: 0 0 40px rgba(0,229,204,0.15), 0 0 80px rgba(0,229,204,0.05);
}
[main.js](https://github.com/user-attachments/files/26130852/main.js)
/* =============================================
   MAIN JS — Clínica Hogar Buena Salud
   ============================================= */

// Resolve data path correctly whether served from /brands/buena-salud/ or root
const DATA_PATH = (() => {
  const p = window.location.pathname;
  if (p.includes('/brands/buena-salud')) return '../../data/buena-salud.json';
  return './data/buena-salud.json';
})();

let DATA = null;

/* ---- Populate HTML from JSON ---- */
function populate(data) {
  DATA = data;

  // KPIs
  const kpiGrid = document.getElementById('kpi-grid');
  if (kpiGrid) {
    kpiGrid.innerHTML = data.kpis.map(k => `
      <div class="kpi-card reveal">
        <span class="kpi-icon">${k.icon}</span>
        <div>
          <span class="kpi-number" data-counter data-target="${k.value}" data-suffix="${k.suffix}">0${k.suffix}</span>
        </div>
        <div class="kpi-label">${k.label}</div>
      </div>
    `).join('');
  }

  // Pillar cards
  const pilaresGrid = document.getElementById('pilares-grid');
  if (pilaresGrid) {
    pilaresGrid.innerHTML = data.pilares.map(p => `
      <div class="pillar-card reveal" style="--pillar-color:${p.color}">
        <div class="pillar-rol" style="color:${p.color}">${p.rol}</div>
        <div class="pillar-nombre">${p.nombre}</div>
        <p class="muted" style="font-size:var(--fs-sm);line-height:1.6">${p.desc}</p>
      </div>
    `).join('');
  }

  // Content stats
  const contenidoList = document.getElementById('contenido-list');
  if (contenidoList) {
    const total = data.contenido.reduce((s, c) => s + c.qty, 0);
    contenidoList.innerHTML = data.contenido.map(c => `
      <div class="stat-bar-wrap reveal">
        <div class="stat-bar-header">
          <div>
            <span class="stat-bar-qty">${c.qty}</span>
            <span class="stat-bar-tipo"> ${c.tipo}</span>
          </div>
        </div>
        <p class="muted" style="font-size:var(--fs-sm);margin-bottom:0.75rem">${c.desc}</p>
        <div class="stat-bar-track">
          <div class="stat-bar-fill" style="width:${(c.qty/total*100).toFixed(0)}%"></div>
        </div>
      </div>
    `).join('');
  }

  // Nichos
  const nichosGrid = document.getElementById('nichos-grid');
  if (nichosGrid) {
    nichosGrid.innerHTML = data.nichos.map(n => `
      <div class="nicho-card reveal">
        <span class="tag ${n.tag === 'B2C' ? 'tag--accent' : n.tag === 'B2B' ? 'tag--purple' : 'tag--amber'}">${n.tag}</span>
        <div class="nicho-nombre">${n.nombre}</div>
        <p class="muted" style="font-size:var(--fs-sm);line-height:1.6">${n.desc}</p>
      </div>
    `).join('');
  }

  // Services
  const serviciosGrid = document.getElementById('servicios-grid');
  if (serviciosGrid) {
    serviciosGrid.innerHTML = data.servicios.map(s => `
      <div class="service-item reveal">
        <span class="service-icon">${s.icon}</span>
        <span>${s.nombre}</span>
      </div>
    `).join('');
  }

  // Price
  const priceAmount = document.getElementById('price-amount');
  const pricePlan = document.getElementById('price-plan');
  if (priceAmount) priceAmount.textContent = data.price;
  if (pricePlan) pricePlan.textContent = data.plan;
}

/* ---- Chart ---- */
function initChart(data) {
  const canvas = document.getElementById('growth-chart');
  if (!canvas || !data) return;

  const ctx = canvas.getContext('2d');
  const accentColor = getComputedStyle(document.documentElement).getPropertyValue('--accent').trim();
  const accent2Color = getComputedStyle(document.documentElement).getPropertyValue('--accent-2').trim();

  const chart = new Chart(ctx, {
    type: 'line',
    data: {
      labels: data.chartLabels,
      datasets: [
        {
          label: 'Crecimiento Orgánico (seguidores)',
          data: data.chartSeguimientoOrganico,
          borderColor: '#00E5CC',
          backgroundColor: 'rgba(0,229,204,0.06)',
          borderWidth: 2,
          pointBackgroundColor: '#00E5CC',
          pointRadius: 4,
          tension: 0.4,
          fill: true,
        },
        {
          label: 'Alcance Pago (Meta Ads)',
          data: data.chartAlcancePagado,
          borderColor: '#7C6DFA',
          backgroundColor: 'rgba(124,109,250,0.06)',
          borderWidth: 2,
          pointBackgroundColor: '#7C6DFA',
          pointRadius: 4,
          tension: 0.4,
          fill: true,
        }
      ]
    },
    options: {
      responsive: true,
      maintainAspectRatio: false,
      animation: { duration: 1500, easing: 'easeOutQuart' },
      plugins: {
        legend: {
          labels: { color: 'rgba(190,220,230,0.7)', font: { family: 'DM Sans', size: 12 }, boxWidth: 12 }
        },
        tooltip: {
          backgroundColor: 'rgba(13,18,32,0.95)',
          borderColor: 'rgba(0,229,204,0.3)',
          borderWidth: 1,
          titleColor: '#EBF4F7',
          bodyColor: 'rgba(190,220,230,0.7)',
          padding: 12,
          callbacks: {
            label: ctx => ` ${ctx.dataset.label}: ${ctx.parsed.y.toLocaleString('es-CL')}`
          }
        }
      },
      scales: {
        x: {
          grid: { color: 'rgba(255,255,255,0.04)' },
          ticks: { color: 'rgba(190,220,230,0.5)', font: { family: 'DM Sans' } }
        },
        y: {
          grid: { color: 'rgba(255,255,255,0.04)' },
          ticks: {
            color: 'rgba(190,220,230,0.5)',
            font: { family: 'DM Sans' },
            callback: v => v.toLocaleString('es-CL')
          }
        }
      }
    }
  });

  // Trigger chart when in viewport
  ScrollTrigger.create({
    trigger: canvas,
    start: 'top 80%',
    once: true,
    onEnter: () => chart.update()
  });
}

/* ---- Stat bars animation ---- */
function initStatBars() {
  document.querySelectorAll('.stat-bar-fill').forEach(bar => {
    ScrollTrigger.create({
      trigger: bar,
      start: 'top 85%',
      once: true,
      onEnter: () => bar.classList.add('is-filled')
    });
  });
}

/* ---- Hero word-by-word animation ---- */
function initHeroAnimation() {
  const tl = gsap.timeline({ defaults: { ease: 'power4.out' } });

  tl.from('.agency-badge', { opacity: 0, y: 20, duration: 0.6 }, 0)
    .from('.hero__title .word', {
      opacity: 0,
      y: 60,
      duration: 0.8,
      stagger: 0.08,
    }, 0.3)
    .from('.hero__sub', { opacity: 0, y: 30, duration: 0.8 }, 0.9)
    .from('.hero__cta', { opacity: 0, y: 20, duration: 0.6 }, 1.2)
    .from('.scroll-cue', { opacity: 0, duration: 0.8 }, 1.6);
}

/* ---- Split title text into words for animation ---- */
function splitWords() {
  document.querySelectorAll('[data-split]').forEach(el => {
    el.innerHTML = el.textContent
      .split(' ')
      .map(w => `<span class="word">${w}&nbsp;</span>`)
      .join('');
  });
}

/* ---- Pinned concept section ---- */
function initPinnedConcept() {
  const section = document.getElementById('concepto');
  if (!section) return;

  const items = section.querySelectorAll('.concepto-item');
  items.forEach((item, i) => {
    gsap.fromTo(item,
      { opacity: 0, x: -40 },
      {
        opacity: 1, x: 0,
        duration: 0.8,
        ease: 'power3.out',
        scrollTrigger: {
          trigger: item,
          start: 'top 80%',
          once: true
        }
      }
    );
  });
}

/* ---- Closing section animation ---- */
function initClosing() {
  const section = document.getElementById('cierre');
  if (!section) return;

  gsap.fromTo('#cierre .close-logo',
    { opacity: 0, scale: 0.8 },
    {
      opacity: 1, scale: 1,
      duration: 1.2,
      ease: 'power3.out',
      scrollTrigger: {
        trigger: '#cierre',
        start: 'top 60%',
        once: true
      }
    }
  );

  gsap.fromTo('#cierre .close-message',
    { opacity: 0, y: 40 },
    {
      opacity: 1, y: 0,
      duration: 1,
      delay: 0.4,
      ease: 'power3.out',
      scrollTrigger: {
        trigger: '#cierre',
        start: 'top 60%',
        once: true
      }
    }
  );
}

/* ---- INIT ---- */
async function init() {
  // Load data
  const data = await PitchCore.loadData(DATA_PATH);
  if (data) populate(data);

  // Core
  PitchCore.initProgressBar();
  PitchCore.initVideoAutoplay();
  PitchCore.initHoverVideos();

  // Brand-specific
  splitWords();
  initHeroAnimation();
  initPinnedConcept();
  initClosing();

  // Wait a tick for DOM to settle after populate
  requestAnimationFrame(() => {
    PitchCore.initReveal();
    PitchCore.initCounters();
    initStatBars();
    if (data) initChart(data);

    const sections = document.querySelectorAll('.section[id]');
    PitchCore.initNavDots(Array.from(sections));

    ScrollTrigger.refresh();
  });
}

document.addEventListener('DOMContentLoaded', init);
[theme.css](https://github.com/user-attachments/files/26130853/theme.css)
/* =============================================
   THEME — Clínica Hogar Buena Salud
   Estética: Médica de alta tecnología.
   Paleta fría con acento teal luminoso.
   Tipografía: Syne (display) + DM Sans (body)
   ============================================= */

@import url('https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500;600&display=swap');

:root {
  /* Override brand colors */
  --bg:           #070B14;
  --bg-2:         #0D1220;
  --bg-3:         #111827;
  --border:       rgba(0,229,204,0.1);
  --border-hover: rgba(0,229,204,0.35);
  --text:         #EBF4F7;
  --text-muted:   rgba(190,220,230,0.5);
  --accent:       #00E5CC;
  --accent-2:     #7C6DFA;
  --accent-3:     #F0A500;
  --accent-glow:  rgba(0,229,204,0.10);

  --font-display: 'Syne', sans-serif;
  --font-body:    'DM Sans', sans-serif;

  /* Brand specific */
  --hero-gradient: linear-gradient(135deg, #070B14 0%, #0D1525 60%, #091A1A 100%);
}

/* ---------- Body bg with subtle grid ---------- */
body {
  background: var(--bg);
  background-image:
    linear-gradient(rgba(0,229,204,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0,229,204,0.03) 1px, transparent 1px);
  background-size: 60px 60px;
}

/* ---------- Hero gradient BG ---------- */
#hero {
  background: var(--hero-gradient);
  position: relative;
  overflow: hidden;
}
#hero::before {
  content: '';
  position: absolute;
  width: 600px; height: 600px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(0,229,204,0.12) 0%, transparent 70%);
  top: -100px; right: -100px;
  pointer-events: none;
}
#hero::after {
  content: '';
  position: absolute;
  width: 400px; height: 400px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(124,109,250,0.08) 0%, transparent 70%);
  bottom: -80px; left: 10%;
  pointer-events: none;
}

/* ---------- Agency badge ---------- */
.agency-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.4rem 1rem;
  border-radius: 100px;
  border: 1px solid var(--accent);
  background: rgba(0,229,204,0.06);
  font-size: var(--fs-xs);
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 1.5rem;
}
.agency-badge::before {
  content: '';
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--accent);
  animation: pulse-dot 2s infinite;
}
@keyframes pulse-dot {
  0%, 100% { opacity: 1; transform: scale(1); }
  50% { opacity: 0.5; transform: scale(1.5); }
}

/* ---------- Hero heading ---------- */
.hero__title {
  font-family: var(--font-display);
  font-size: clamp(2.8rem, 7vw, 6.5rem);
  font-weight: 800;
  line-height: 1.0;
  letter-spacing: -0.03em;
  color: var(--text);
}
.hero__title .line { overflow: hidden; display: block; }
.hero__title .word { display: inline-block; }
.hero__sub {
  font-size: var(--fs-lg);
  color: var(--text-muted);
  max-width: 600px;
  line-height: 1.6;
  margin-top: 1.5rem;
}

/* ---------- Hero scroll cue ---------- */
.scroll-cue {
  position: absolute;
  bottom: 2.5rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  font-size: var(--fs-xs);
  color: var(--text-muted);
  letter-spacing: 0.1em;
  text-transform: uppercase;
}
.scroll-cue__arrow {
  width: 1px;
  height: 40px;
  background: linear-gradient(180deg, var(--accent), transparent);
  animation: scroll-line 2s ease-in-out infinite;
}
@keyframes scroll-line {
  0% { transform: scaleY(0); transform-origin: top; }
  50% { transform: scaleY(1); transform-origin: top; }
  51% { transform-origin: bottom; }
  100% { transform: scaleY(0); transform-origin: bottom; }
}

/* ---------- Pillar Cards ---------- */
.pillar-card {
  position: relative;
  padding: 2rem;
  border-radius: var(--radius);
  background: var(--bg-2);
  border: 1px solid var(--border);
  overflow: hidden;
  transition: border-color 0.4s, transform 0.4s var(--ease);
}
.pillar-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: var(--pillar-color);
  opacity: 0.7;
}
.pillar-card:hover {
  border-color: var(--pillar-color);
  transform: translateY(-6px);
}
.pillar-rol {
  font-size: var(--fs-xs);
  font-weight: 700;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}
.pillar-nombre {
  font-family: var(--font-display);
  font-size: var(--fs-xl);
  font-weight: 700;
  margin-bottom: 1rem;
  line-height: 1.2;
}

/* ---------- Content Stat Bars ---------- */
.stat-bar-wrap { margin-bottom: 1.5rem; }
.stat-bar-header {
  display: flex;
  justify-content: space-between;
  align-items: baseline;
  margin-bottom: 0.5rem;
}
.stat-bar-qty {
  font-family: var(--font-display);
  font-size: 2.5rem;
  font-weight: 800;
  color: var(--accent);
  line-height: 1;
}
.stat-bar-tipo {
  font-weight: 600;
  font-size: var(--fs-lg);
}
.stat-bar-track {
  height: 4px;
  background: rgba(255,255,255,0.06);
  border-radius: 100px;
  overflow: hidden;
}
.stat-bar-fill {
  height: 100%;
  border-radius: 100px;
  background: linear-gradient(90deg, var(--accent), var(--accent-2));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 1.2s var(--ease);
}
.stat-bar-fill.is-filled { transform: scaleX(1); }

/* ---------- Nicho cards ---------- */
.nicho-card {
  background: var(--bg-2);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 1.5rem;
  transition: border-color 0.4s, transform 0.3s var(--ease);
}
.nicho-card:hover {
  border-color: var(--border-hover);
  transform: translateY(-4px);
}
.nicho-nombre {
  font-family: var(--font-display);
  font-size: var(--fs-xl);
  font-weight: 700;
  margin: 0.75rem 0 0.5rem;
}

/* ---------- Service grid ---------- */
.service-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem 1.25rem;
  background: var(--bg-2);
  border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  font-weight: 500;
  transition: background 0.3s, border-color 0.3s;
}
.service-item:hover {
  background: var(--bg-3);
  border-color: var(--border-hover);
}
.service-icon {
  color: var(--accent);
  font-size: 1.1rem;
  flex-shrink: 0;
  width: 28px;
  text-align: center;
}

/* ---------- Chart Section ---------- */
.chart-container {
  position: relative;
  height: 320px;
}

/* ---------- Price Card ---------- */
.price-card {
  background: linear-gradient(135deg, var(--bg-2), var(--bg-3));
  border: 1px solid var(--accent);
  border-radius: var(--radius-lg);
  padding: 3rem;
  text-align: center;
  position: relative;
  overflow: hidden;
  box-shadow: 0 0 60px rgba(0,229,204,0.08), 0 0 120px rgba(0,229,204,0.04);
}
.price-card::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse at 50% 0%, rgba(0,229,204,0.06), transparent 60%);
}
.price-amount {
  font-family: var(--font-display);
  font-size: clamp(2.5rem, 5vw, 4.5rem);
  font-weight: 800;
  color: var(--accent);
  letter-spacing: -0.03em;
  line-height: 1.1;
}
.price-period {
  color: var(--text-muted);
  font-size: var(--fs-lg);
  margin-top: 0.25rem;
}
.price-plan {
  font-family: var(--font-display);
  font-size: var(--fs-sm);
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--text-muted);
  margin-bottom: 1rem;
}

/* ---------- Closing section ---------- */
#cierre {
  background: radial-gradient(ellipse at 50% 50%, rgba(0,229,204,0.06) 0%, transparent 70%), var(--bg);
}

/* ---------- Section titles ---------- */
.section-eyebrow {
  font-size: var(--fs-xs);
  font-weight: 700;
  letter-spacing: 0.18em;
  text-transform: uppercase;
  color: var(--accent);
  margin-bottom: 0.75rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.section-eyebrow::before {
  content: '';
  display: inline-block;
  width: 24px; height: 1px;
  background: var(--accent);
}

/* ---------- Floating decoration lines ---------- */
.deco-line {
  position: absolute;
  pointer-events: none;
  opacity: 0.15;
}

@media (max-width: 768px) {
  .hero__title { font-size: clamp(2.2rem, 10vw, 3.5rem); }
  .price-card { padding: 2rem 1.5rem; }
}
[index (1).html](https://github.com/user-attachments/files/26130855/index.1.html)
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Clínica Hogar Buena Salud × DualMac — Plan Black</title>
  <meta name="description" content="Propuesta estratégica de comunicación digital para Clínica Hogar Buena Salud." />

  <!-- Shared base styles -->
  <link rel="stylesheet" href="../../shared/css/base.css" />
  <!-- Brand theme -->
  <link rel="stylesheet" href="css/theme.css" />

  <!-- GSAP + ScrollTrigger -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js" defer></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js" defer></script>
  <!-- Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.3/dist/chart.umd.min.js" defer></script>
  <!-- Core + Main -->
  <script src="../../shared/js/core.js" defer></script>
  <script src="js/main.js" defer></script>
</head>
<body class="noise">

  <!-- Progress bar -->
  <div id="progress-bar"></div>

  <!-- Nav dots (populated by JS) -->
  <nav id="nav-dots" aria-label="Navegación de secciones"></nav>

  <!-- ============================================================
       SECCIÓN 1: HERO
       ============================================================ -->
  <section class="section" id="hero" style="min-height:100vh; display:flex; align-items:center;">
    <div class="container" style="padding-block: var(--sp-xl);">
      <div style="max-width: 820px;">

        <div class="agency-badge">DualMac · Propuesta Estratégica</div>

        <h1 class="hero__title" aria-label="Clínica Hogar Buena Salud">
          <span class="line">
            <span class="word">Clínica</span>
            <span class="word" style="color:var(--accent)">Hogar</span>
          </span>
          <span class="line">
            <span class="word">Buena</span>
            <span class="word">Salud.</span>
          </span>
        </h1>

        <p class="hero__sub">
          Donde la recuperación deja de ser una posibilidad
          y se convierte en un proceso real, acompañado y medible.
        </p>

        <div class="hero__cta" style="margin-top: 2.5rem; display:flex; gap:1rem; flex-wrap:wrap; align-items:center;">
          <a href="#concepto"
             style="display:inline-flex; align-items:center; gap:0.5rem; padding:0.8rem 1.75rem;
                    background:var(--accent); color:var(--bg); border-radius:100px;
                    font-weight:700; font-size:var(--fs-sm); letter-spacing:0.04em;
                    transition: transform 0.3s, box-shadow 0.3s;"
             onmouseover="this.style.transform='translateY(-2px)';this.style.boxShadow='0 8px 32px rgba(0,229,204,0.35)'"
             onmouseout="this.style.transform='';this.style.boxShadow=''">
            Ver propuesta ↓
          </a>
          <span style="color:var(--text-muted); font-size:var(--fs-sm)">
            Plan Black · 2025
          </span>
        </div>

        <!-- Mini stats preview -->
        <div style="margin-top: 3.5rem; display:flex; gap:2.5rem; flex-wrap:wrap;">
          <div>
            <div style="font-family:var(--font-display); font-size:2rem; font-weight:800; color:var(--accent)">36</div>
            <div style="font-size:var(--fs-xs); color:var(--text-muted); letter-spacing:0.06em; text-transform:uppercase">Piezas / mes</div>
          </div>
          <div style="width:1px; background:var(--border);"></div>
          <div>
            <div style="font-family:var(--font-display); font-size:2rem; font-weight:800; color:var(--accent-2)">+116%</div>
            <div style="font-size:var(--fs-xs); color:var(--text-muted); letter-spacing:0.06em; text-transform:uppercase">Presencia digital</div>
          </div>
          <div style="width:1px; background:var(--border);"></div>
          <div>
            <div style="font-family:var(--font-display); font-size:2rem; font-weight:800; color:var(--accent-3)">2K+</div>
            <div style="font-size:var(--fs-xs); color:var(--text-muted); letter-spacing:0.06em; text-transform:uppercase">Seguidores / mes</div>
          </div>
        </div>
      </div>
    </div>

    <div class="scroll-cue">
      <span>scroll</span>
      <div class="scroll-cue__arrow"></div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 2: CONCEPTO ESTRATÉGICO
       ============================================================ -->
  <section class="section" id="concepto">
    <div class="container">
      <div style="max-width:740px; margin-bottom: var(--sp-lg);">
        <p class="section-eyebrow reveal">01 — Concepto Estratégico</p>
        <h2 class="heading reveal" style="margin-bottom:1.25rem;">
          El crecimiento no depende de mejorar el servicio clínico.
        </h2>
        <p class="muted reveal" style="font-size:var(--fs-lg); line-height:1.7;">
          Depende de cómo ese valor se <strong style="color:var(--text)">comunica, se percibe</strong> y se transforma en decisiones.
        </p>
      </div>

      <!-- Quote highlight -->
      <div class="reveal" style="
        border-left: 3px solid var(--accent);
        padding: 1.5rem 2rem;
        background: rgba(0,229,204,0.04);
        border-radius: 0 var(--radius) var(--radius) 0;
        margin-bottom: var(--sp-lg);
        max-width: 800px;">
        <p style="font-family:var(--font-display); font-size:clamp(1.1rem, 2.5vw, 1.5rem); font-weight:600; line-height:1.5; color:var(--text);">
          "Donde la recuperación deja de ser una posibilidad y se convierte en un proceso real, acompañado y medible."
        </p>
        <p class="muted" style="margin-top:0.75rem; font-size:var(--fs-sm)">Concepto central de marca · Clínica Hogar Buena Salud</p>
      </div>

      <!-- Three pillars — populated by JS -->
      <p class="section-eyebrow reveal" style="margin-bottom:1rem;">Tres pilares fundamentales</p>
      <div class="grid-3" id="pilares-grid">
        <!-- JS inject -->
      </div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 3: COMUNICACIÓN DIGITAL
       ============================================================ -->
  <section class="section" id="comunicacion" style="background: var(--bg-2);">
    <div class="container">
      <div style="max-width:680px; margin-bottom: var(--sp-lg);">
        <p class="section-eyebrow reveal">02 — Comunicación Digital</p>
        <h2 class="heading reveal">
          No necesitas más publicaciones.<br/>
          Necesitas comunicar <span class="grad-text">estratégicamente.</span>
        </h2>
      </div>

      <div class="grid-2" style="gap: var(--sp-lg); align-items:start;">

        <!-- Left: content stat bars -->
        <div>
          <p class="muted reveal" style="margin-bottom:2rem; font-size:var(--fs-lg); line-height:1.7;">
            Todo lo que ocurre dentro de la clínica se transforma en contenido, y ese contenido en pacientes.
          </p>
          <div id="contenido-list"><!-- JS inject --></div>
        </div>

        <!-- Right: content strategy cards -->
        <div style="display:flex; flex-direction:column; gap:1rem;">
          <div class="concepto-item card reveal" style="border-left:2px solid var(--accent);">
            <div style="font-weight:700; margin-bottom:0.5rem; display:flex; gap:0.5rem; align-items:center;">
              <span style="color:var(--accent)">01</span> Mostrar resultados reales
            </div>
            <p class="muted" style="font-size:var(--fs-sm)">Pacientes que vuelven a caminar, recuperan el habla. Evolución del proceso. Esto es lo que más convierte.</p>
          </div>
          <div class="concepto-item card reveal">
            <div style="font-weight:700; margin-bottom:0.5rem; display:flex; gap:0.5rem; align-items:center;">
              <span style="color:var(--accent-2)">02</span> Educar al paciente y familia
            </div>
            <p class="muted" style="font-size:var(--fs-sm)">¿Qué es la neurorrehabilitación? ¿Qué hacer después de un ACV? Genera confianza antes del contacto.</p>
          </div>
          <div class="concepto-item card reveal">
            <div style="font-weight:700; margin-bottom:0.5rem; display:flex; gap:0.5rem; align-items:center;">
              <span style="color:var(--accent-3)">03</span> Humanizar la clínica
            </div>
            <p class="muted" style="font-size:var(--fs-sm)">Equipo médico, terapias, día a día. Participación familiar. Cercanía y conexión emocional.</p>
          </div>
          <div class="concepto-item card reveal">
            <div style="font-weight:700; margin-bottom:0.5rem; display:flex; gap:0.5rem; align-items:center;">
              <span style="color:var(--accent)">04</span> Diferenciación técnica
            </div>
            <p class="muted" style="font-size:var(--fs-sm)">TrainFES, fisiatra, metodología interdisciplinaria. Posiciona como clínica de alto nivel.</p>
          </div>
        </div>

      </div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 4: NICHOS
       ============================================================ -->
  <section class="section" id="nichos">
    <div class="container">
      <div style="max-width:620px; margin-bottom:var(--sp-lg);">
        <p class="section-eyebrow reveal">03 — Segmentos Target</p>
        <h2 class="heading reveal">
          La estrategia apunta a nichos con alta probabilidad de conversión.
        </h2>
      </div>
      <div class="grid-3" id="nichos-grid"><!-- JS inject --></div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 5: PLAN BLACK — PRODUCCIÓN MENSUAL
       ============================================================ -->
  <section class="section" id="plan" style="background: var(--bg-2);">
    <div class="container">
      <div style="max-width:680px; margin-bottom:var(--sp-lg);">
        <p class="section-eyebrow reveal">04 — Plan Black</p>
        <h2 class="heading reveal">
          Ejecución estratégica.<br/>
          <span class="grad-text">Te ayudamos a vender mejor.</span>
        </h2>
        <p class="muted reveal" style="margin-top:1rem; font-size:var(--fs-lg);">
          36 piezas de contenido mensual · +116% presencia digital
        </p>
      </div>

      <!-- Content breakdown visual -->
      <div style="display:grid; grid-template-columns: repeat(3,1fr); gap:1rem; margin-bottom:var(--sp-lg);">
        <div class="reveal" style="background:var(--bg-3); border:1px solid var(--border); border-radius:var(--radius); padding:2rem; text-align:center; position:relative; overflow:hidden;">
          <div style="position:absolute;top:0;left:0;right:0;height:2px;background:var(--accent);"></div>
          <div style="font-family:var(--font-display);font-size:3.5rem;font-weight:800;color:var(--accent);line-height:1;">12</div>
          <div style="font-weight:700;margin:0.5rem 0 0.25rem">Posts</div>
          <p class="muted" style="font-size:var(--fs-xs)">Cápsulas estratégicas de posicionamiento</p>
        </div>
        <div class="reveal" style="background:var(--bg-3); border:1px solid var(--border); border-radius:var(--radius); padding:2rem; text-align:center; position:relative; overflow:hidden;">
          <div style="position:absolute;top:0;left:0;right:0;height:2px;background:var(--accent-2);"></div>
          <div style="font-family:var(--font-display);font-size:3.5rem;font-weight:800;color:var(--accent-2);line-height:1;">16</div>
          <div style="font-weight:700;margin:0.5rem 0 0.25rem">Historias</div>
          <p class="muted" style="font-size:var(--fs-xs)">Presencia diaria y recordación de marca</p>
        </div>
        <div class="reveal" style="background:var(--bg-3); border:1px solid var(--border); border-radius:var(--radius); padding:2rem; text-align:center; position:relative; overflow:hidden;">
          <div style="position:absolute;top:0;left:0;right:0;height:2px;background:var(--accent-3);"></div>
          <div style="font-family:var(--font-display);font-size:3.5rem;font-weight:800;color:var(--accent-3);line-height:1;">8</div>
          <div style="font-weight:700;margin:0.5rem 0 0.25rem">Reels</div>
          <p class="muted" style="font-size:var(--fs-xs)">4 con IA: avatares, UGC, edición avanzada</p>
        </div>
      </div>

      <!-- Services grid -->
      <p class="section-eyebrow reveal" style="margin-bottom:1rem;">Servicios incluidos</p>
      <div style="display:grid; grid-template-columns:repeat(auto-fit, minmax(240px,1fr)); gap:0.75rem;" id="servicios-grid">
        <!-- JS inject -->
      </div>

      <!-- Additional services list -->
      <div style="margin-top:var(--sp-md); display:grid; grid-template-columns:repeat(auto-fit,minmax(260px,1fr)); gap:1rem;">
        <div class="reveal card">
          <div class="section-eyebrow" style="margin-bottom:0.75rem;">📲 Meta Ads</div>
          <p class="muted" style="font-size:var(--fs-sm);">Campañas orientadas a conversión. Segmentación inteligente, geolocalización, generación de leads calificados.</p>
        </div>
        <div class="reveal card">
          <div class="section-eyebrow" style="margin-bottom:0.75rem;">🧠 IA + Tecnología</div>
          <p class="muted" style="font-size:var(--fs-sm);">Atracción de 1.000–2.000 seguidores mensuales. Optimización basada en datos reales y análisis de competencia.</p>
        </div>
        <div class="reveal card">
          <div class="section-eyebrow" style="margin-bottom:0.75rem;">📊 Reportes + Reuniones</div>
          <p class="muted" style="font-size:var(--fs-sm);">Mínimo 3 reuniones al mes. Métricas claras, seguimiento constante y escalamiento de lo que funciona.</p>
        </div>
      </div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 6: KPIs
       ============================================================ -->
  <section class="section" id="kpis">
    <div class="container">
      <div style="max-width:640px; margin-bottom:var(--sp-lg);">
        <p class="section-eyebrow reveal">05 — Resultados</p>
        <h2 class="heading reveal">
          Números que definen el impacto.
        </h2>
      </div>
      <div class="kpi-grid" id="kpi-grid">
        <!-- JS inject -->
      </div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 7: GRÁFICO DE CRECIMIENTO
       ============================================================ -->
  <section class="section" id="crecimiento" style="background:var(--bg-2);">
    <div class="container">
      <div style="max-width:640px; margin-bottom:var(--sp-lg);">
        <p class="section-eyebrow reveal">06 — Proyección de Crecimiento</p>
        <h2 class="heading reveal">
          Crecimiento orgánico + pago.<br/>
          <span class="grad-text">Semestre 1.</span>
        </h2>
        <p class="muted reveal" style="margin-top:1rem;">Proyección estimada basada en estrategia activa de contenido y campañas Meta Ads optimizadas.</p>
      </div>
      <div class="reveal" style="
        background:var(--bg-3);
        border:1px solid var(--border);
        border-radius:var(--radius-lg);
        padding: var(--sp-md);
      ">
        <div class="chart-container">
          <canvas id="growth-chart"></canvas>
        </div>
      </div>
      <div style="display:flex; gap:2rem; flex-wrap:wrap; margin-top:1.5rem;">
        <div class="reveal" style="display:flex;align-items:center;gap:0.5rem;">
          <div style="width:12px;height:12px;border-radius:50%;background:var(--accent);flex-shrink:0;"></div>
          <span class="muted" style="font-size:var(--fs-sm)">Crecimiento orgánico (seguidores acumulados)</span>
        </div>
        <div class="reveal" style="display:flex;align-items:center;gap:0.5rem;">
          <div style="width:12px;height:12px;border-radius:50%;background:var(--accent-2);flex-shrink:0;"></div>
          <span class="muted" style="font-size:var(--fs-sm)">Alcance pagado (Meta Ads)</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 8: INVERSIÓN
       ============================================================ -->
  <section class="section" id="inversion">
    <div class="container">
      <div style="max-width:640px; margin:0 auto; text-align:center;">
        <p class="section-eyebrow reveal" style="justify-content:center;">07 — Inversión</p>
        <h2 class="heading reveal" style="margin-bottom:var(--sp-lg);">
          Un sistema completo.<br/>
          Un solo precio.
        </h2>

        <div class="price-card reveal">
          <div class="price-plan" id="price-plan">Plan Black</div>
          <div class="price-amount" id="price-amount">$2.189.981 CLP</div>
          <div class="price-period">mensuales</div>

          <div class="divider" style="margin-block:1.5rem;"></div>

          <div style="display:grid; grid-template-columns:1fr 1fr; gap:0.75rem; text-align:left; font-size:var(--fs-sm);">
            <div style="display:flex;gap:0.5rem;align-items:flex-start;">
              <span style="color:var(--accent)">✓</span>
              <span class="muted">36 piezas de contenido</span>
            </div>
            <div style="display:flex;gap:0.5rem;align-items:flex-start;">
              <span style="color:var(--accent)">✓</span>
              <span class="muted">Meta Ads + segmentación</span>
            </div>
            <div style="display:flex;gap:0.5rem;align-items:flex-start;">
              <span style="color:var(--accent)">✓</span>
              <span class="muted">Estrategia + planificación</span>
            </div>
            <div style="display:flex;gap:0.5rem;align-items:flex-start;">
              <span style="color:var(--accent)">✓</span>
              <span class="muted">IA + tecnología avanzada</span>
            </div>
            <div style="display:flex;gap:0.5rem;align-items:flex-start;">
              <span style="color:var(--accent)">✓</span>
              <span class="muted">Reportes + reuniones (×3/mes)</span>
            </div>
            <div style="display:flex;gap:0.5rem;align-items:flex-start;">
              <span style="color:var(--accent)">✓</span>
              <span class="muted">Monitoreo continuo</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ============================================================
       SECCIÓN 9: CIERRE
       ============================================================ -->
  <section class="section section--center" id="cierre">
    <div class="container" style="display:flex;flex-direction:column;align-items:center;gap:2rem;text-align:center;">

      <!-- Logo mark -->
      <div class="close-logo" style="
        width: 100px; height: 100px;
        border: 1.5px solid var(--accent);
        border-radius: 50%;
        display:flex; align-items:center; justify-content:center;
        font-size: 2.5rem;
        box-shadow: 0 0 40px rgba(0,229,204,0.2), 0 0 80px rgba(0,229,204,0.08);
        color: var(--accent);
      ">✦</div>

      <div class="close-message">
        <h2 class="heading" style="font-size:clamp(2rem, 5vw, 4rem); max-width:700px; margin:0 auto 1.5rem;">
          Convertimos tu valor clínico en <span class="grad-text">pacientes reales.</span>
        </h2>
        <p class="muted" style="font-size:var(--fs-lg); max-width:500px; margin:0 auto 2rem; line-height:1.7;">
          DualMac diseña el sistema estratégico que conecta a Buena Salud con las personas que la necesitan.
        </p>

        <div style="display:flex; gap:1rem; justify-content:center; flex-wrap:wrap;">
          <a href="mailto:hola@dualmac.com"
             style="padding:0.9rem 2rem; background:var(--accent); color:var(--bg);
                    border-radius:100px; font-weight:700; font-size:var(--fs-sm);
                    transition:transform 0.3s, box-shadow 0.3s; display:inline-block;"
             onmouseover="this.style.transform='translateY(-2px)';this.style.boxShadow='0 8px 32px rgba(0,229,204,0.35)'"
             onmouseout="this.style.transform='';this.style.boxShadow=''">
            Hablemos
          </a>
          <a href="#hero"
             style="padding:0.9rem 2rem; background:transparent; color:var(--text);
                    border:1px solid var(--border-hover); border-radius:100px; font-weight:600;
                    font-size:var(--fs-sm); transition:border-color 0.3s; display:inline-block;"
             onmouseover="this.style.borderColor='var(--accent)'"
             onmouseout="this.style.borderColor='var(--border-hover)'">
            Ver desde el inicio ↑
          </a>
        </div>
      </div>

      <!-- Footer -->
      <div style="margin-top:var(--sp-xl); padding-top:var(--sp-md); border-top:1px solid var(--border); width:100%; display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:1rem;">
        <span class="muted" style="font-size:var(--fs-xs)">DualMac · Agencia de Marketing Digital</span>
        <span class="muted" style="font-size:var(--fs-xs)">Clínica Hogar Buena Salud · Plan Black · 2025</span>
        <a href="../../index.html" class="muted" style="font-size:var(--fs-xs); transition:color 0.2s;"
           onmouseover="this.style.color='var(--accent)'" onmouseout="this.style.color=''">
          ← Otras propuestas
        </a>
      </div>
    </div>
  </section>

</body>
</html>


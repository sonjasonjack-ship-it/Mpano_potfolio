<script>
import bravo from "@/public/bravo.png"
</script>
<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

// 1. Hero Slideshow hamwe n'amafoto y'imishinga
const heroSlides = ref([
  {
    badge: 'L4 SOFTWARE DEVELOPMENT • COLLÈGE DE BETHEL',
    title: 'MPANO Jabo Jackson',
    subtitle: 'Full-Stack Web Developer & Systems Enthusiast. Nkubaka imbuga zifite amashusho meza, zihuta, kandi zikorana n’ikoranabuhanga rigezweho.',
    highlight: 'Engineering the Digital Future',
    image: 'https://images.unsplash.com/photo-1555066931-4365d14bab8c?auto=format&fit=crop&w=800&q=80'
  },
  {
    badge: 'FRONTEND & UI/UX DESIGN',
    title: 'Modern, Responsive & Animated Interfaces',
    subtitle: 'Gushushanya imbuga zifite amashusho meza, animations zidasanzwe, na responsive design ikora kuri buri mudasobwa na telefone.',
    highlight: 'Vue 3 • CSS3 • Visual UI/UX',
    image: 'https://images.unsplash.com/photo-1507238691740-187a5b1d37b8?auto=format&fit=crop&w=800&q=80'
  },
  {
    badge: 'BACKEND, DATABASES & NETWORKING',
    title: 'Robust Systems & Database Architecture',
    subtitle: 'Gucunga za Server, Node.js, PHP, MySQL, hamwe na Windows Server Active Directory ku bigo by’amashuri.',
    highlight: 'Node.js • PHP • MySQL • Windows Server',
    image: 'https://images.unsplash.com/photo-1526374965328-7f61d4dc18c5?auto=format&fit=crop&w=800&q=80'
  }
]);

const currentHeroSlide = ref(0);

// 2. Imishinga irimo amafoto
const projects = ref([
  {
    number: '01',
    category: 'School Management System',
    title: 'ASPADE Ngororero School Portal',
    description: 'Sisitemu icunga ibigo by’amashuri irimo kwandika abanyeshuri online, Admin Dashboard yo kugenzura ubusabe, guhitamo intara n’uturere (georwanda), no kohereza ubutumwa bugufi (SMS).',
    tech: ['Vue 3', 'Node.js', 'Express.js', 'MySQL', 'SMS API'],
    image: 'https://images.unsplash.com/photo-1517694712202-14dd9538aa97?auto=format&fit=crop&w=900&q=80'
  },
  {
    number: '02',
    category: 'Entertainment & Streaming',
    title: 'Bravo.net Streaming Platform',
    description: 'Urubuga rwa filime na series (bravo.net) rukoresha TMDB API, rufite Dark Mode nziza, gushakisha byihuse, na animations zigezweho.',
    tech: ['Vue 3', 'Vite', 'TMDB API', 'Vue Router'],
    image: 'bravo'
  },
  {
    number: '03',
    category: 'Systems & Infrastructure',
    title: 'Offline LAN & Active Directory Lab',
    description: 'Gutunganya imiyoboro ya mudasobwa nta interineti ihari, gushyiraho Windows Server Active Directory Domains, no gukoresha Kali Linux.',
    tech: ['Windows Server', 'Active Directory', 'PHP', 'Kali Linux'],
    image: 'https://images.unsplash.com/photo-1544197150-b99a580bb7a8?auto=format&fit=crop&w=900&q=80'
  },
  {
    number: '04',
    category: 'School Communication',
    title: 'Classroom Intercom Web System',
    description: 'Igishushanyo cya porogaramu ifasha umuyobozi ushinzwe amasomo (DOS) guhamagara abanyeshuri mu mashuri yabo akoresheje mikoro yo ku biro.',
    tech: ['UI/UX Design', 'Web Audio API', 'Vue.js'],
    image: 'https://images.unsplash.com/photo-1581092160607-ee22621dd758?auto=format&fit=crop&w=900&q=80'
  }
]);

const currentProject = ref(0);

// 3. Ubumenyi
const skills = ref([
  {
    title: 'Frontend Engineering',
    desc: 'Kubaka imbuga zifite isura nziza n’umuvuduko wo hejuru.',
    list: ['Vue.js 3 (Composition API)', 'HTML5 & Advanced CSS3', 'Keyframe Animations & Transitions', 'Responsive Mobile-First Design']
  },
  {
    title: 'Backend & Databases',
    desc: 'Gukora za Server, APIs, na MySQL databases.',
    list: ['Node.js & Express.js', 'PHP Programming', 'MySQL Relational Databases', 'ERD Database Design (Lucidchart)']
  },
  {
    title: 'Systems & Tools',
    desc: 'Gucunga operating systems na tools za developers.',
    list: ['Windows Server (Active Directory)', 'Linux Terminal & Kali', 'Git, GitHub & Vercel Deployment', 'Number Base Systems (Octal/Binary)']
  }
]);

// 4. Services
const services = ref([
  {
    icon: '⚡',
    title: 'Full-Stack Web Development',
    detail: 'Kubaka imbuga zikora kuva hasi kugeza hejuru zihujwe na database ya MySQL.'
  },
  {
    icon: '🎨',
    title: 'Modern UI & Animations',
    detail: 'Gushushanya amabara, typography, na CSS animations zikurura abantu.'
  },
  {
    icon: '🗄️',
    title: 'Database & Server Setup',
    detail: 'Gutegura ERD diagrams, Windows Server, na za local LAN environments.'
  }
]);

// Download Real PDF CV Function
const downloadCV = () => {
  const link = document.createElement('a');
  link.href = '.\public\MPANO Jabo Jackson _cv.pdf'; // Hitamo ko iyi PDF iri muri public folder ya project yawe
  link.download = 'MPANO Jabo Jackson _cv.pdf';
  document.body.appendChild(link);
  link.click();
  document.body.removeChild(link);
};

let heroTimer = null;
let projectTimer = null;

const nextHero = () => {
  currentHeroSlide.value = (currentHeroSlide.value + 1) % heroSlides.value.length;
};
const prevHero = () => {
  currentHeroSlide.value = (currentHeroSlide.value - 1 + heroSlides.value.length) % heroSlides.value.length;
};

const nextProject = () => {
  currentProject.value = (currentProject.value + 1) % projects.value.length;
};
const prevProject = () => {
  currentProject.value = (currentProject.value - 1 + projects.value.length) % projects.value.length;
};

onMounted(() => {
  heroTimer = setInterval(nextHero, 6000);
  projectTimer = setInterval(nextProject, 5500);
});

onUnmounted(() => {
  clearInterval(heroTimer);
  clearInterval(projectTimer);
});
</script>

<template>
  <div class="app-container">
    <div class="bg-glow glow-1"></div>
    <div class="bg-glow glow-2"></div>

    <!-- Navbar -->
    <nav class="navbar">
      <div class="nav-inner">
        <div class="brand">
          <span class="brand-dot"></span>
          MPANO<span class="accent">.JACKSON</span>
        </div>
        <ul class="nav-menu">
          <li><a href="#home">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#education">Education</a></li>
          <li><a href="#skills">Skills</a></li>
          <li><a href="#projects">Projects</a></li>
          <li><a href="#contact" class="nav-cta">Get in Touch</a></li>
        </ul>
      </div>
    </nav>

    <!-- HERO SECTION WITH IMAGES -->
    <header id="home" class="hero-fullscreen">
      <div class="hero-inner">
        <transition name="hero-slide" mode="out-in">
          <div :key="currentHeroSlide" class="hero-slide-grid">
            <div class="hero-slide-content">
              <div class="hero-badge">{{ heroSlides[currentHeroSlide].badge }}</div>
              <h1 class="hero-title">{{ heroSlides[currentHeroSlide].title }}</h1>
              <h2 class="hero-highlight">{{ heroSlides[currentHeroSlide].highlight }}</h2>
              <p class="hero-desc">{{ heroSlides[currentHeroSlide].subtitle }}</p>
              
              <div class="hero-actions">
                
                <a href="../public/MPANO Jabo Jackson _cv.pdf" download="MPANO_Jabo_Jackson_CV.pdf" class="btn-outline cv-btn">
  <span>📄</span> Download CV (PDF)
</a>
              </div>
            </div>

            <div class="hero-image-frame">
              <img :src="heroSlides[currentHeroSlide].image" alt="Portfolio Showcase" class="hero-img" />
              <div class="img-badge-overlay">
                <span>⭐ L4 SOD Developer</span>
              </div>
            </div>
          </div>
        </transition>

        <div class="hero-controls">
          <button @click="prevHero" class="arrow-btn" aria-label="Previous Slide">&#8592;</button>
          <div class="hero-indicators">
            <span 
              v-for="(s, idx) in heroSlides" 
              :key="idx" 
              class="bar" 
              :class="{ active: currentHeroSlide === idx }"
              @click="currentHeroSlide = idx"
            ></span>
          </div>
          <button @click="nextHero" class="arrow-btn" aria-label="Next Slide">&#8594;</button>
        </div>
      </div>

      <div class="stats-strip">
        <div class="stat-item">
          <span class="stat-val">L4 SOD</span>
          <span class="stat-label">Software Development</span>
        </div>
        <div class="stat-item">
          <span class="stat-val">Collège de Bethel</span>
          <span class="stat-label">Current Institution</span>
        </div>
        <div class="stat-item">
          <span class="stat-val">GS RUHANGO ADEPR</span>
          <span class="stat-label">Foundation School</span>
        </div>
        <div class="stat-item">
          <span class="stat-val">Full-Stack</span>
          <span class="stat-label">Vue • Node • PHP • MySQL</span>
        </div>
      </div>
    </header>

    <!-- ABOUT SECTION -->
    <section id="about" class="full-section">
      <div class="section-container">
        <div class="section-header">
          <span class="sub-tag">BIOGRAPHY & PROFILE</span>
          <h2>Who I Am & What I Do</h2>
        </div>

        <div class="about-grid">
          <div class="about-text-card">
            <h3>Hello! I am <span class="text-emerald">MPANO Jabo Jackson</span>[cite: 2]</h3>
            <p>
              Ndi umunyeshuri wiga mu mwaka wa kane mu ishami rya <strong>Software Development (L4 SOD)</strong> kuri <strong>Collège de Bethel</strong>, nyuma yo gusoza icyiciro cya mbere kuri <strong>GS RUHANGO ADEPR</strong>[cite: 2].
            </p>
            <p>
              Mfite ishyaka mu kubaka imbuga zifite isura nziza, imikorere yihuse, hamwe na porogaramu zikora mu buryo bwa Offline-first[cite: 2].
            </p>
            <div class="terminal-box">
              <div class="term-header">
                <span class="t-dot emerald"></span>
                <span class="t-dot gold"></span>
                <span class="t-dot gray"></span>
                <span class="term-title">jackson@bethel-l4sod:~</span>
              </div>
              <pre><code>$ whoami
> MPANO Jabo Jackson (Full-Stack Developer)
$ cat skills.txt
> Vue.js 3, CSS3, Node.js, Express, PHP, MySQL, Windows Server</code></pre>
            </div>
          </div>

          <div class="services-column">
            <div v-for="(srv, i) in services" :key="i" class="service-card">
              <div class="srv-icon">{{ srv.icon }}</div>
              <div>
                <h4>{{ srv.title }}</h4>
                <p>{{ srv.detail }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- EDUCATION SECTION -->
    <section id="education" class="full-section alt-bg">
      <div class="section-container">
        <div class="section-header">
          <span class="sub-tag">ACADEMIC JOURNEY</span>
          <h2>Education & Background</h2>
        </div>

        <div class="edu-grid">
          <div class="edu-card active-edu">
            <div class="edu-badge">CURRENT • LEVEL 4 SOD</div>
            <h3>Collège de Bethel[cite: 2]</h3>
            <p class="edu-program">Software Development (L4 SOD)[cite: 2]</p>
            <p class="edu-details">
              Kwiga kubaka imbuga (Frontend & Backend), gucunga database za MySQL na ERDs, gushyiraho Windows Server Active Directory, hamwe na Linux[cite: 2].
            </p>
          </div>

          <div class="edu-card">
            <div class="edu-badge gold-badge">FOUNDATION EDUCATION</div>
            <h3>GS RUHANGO ADEPR[cite: 2]</h3>
            <p class="edu-program">O-Level General Education[cite: 2]</p>
            <p class="edu-details">
              Aho natangiriye urugendo rwanjye rw'amashuri yisumbuye nka foundation ikomeye mu bumenyi n'ikoranabuhanga[cite: 2].
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- SKILLS SECTION -->
    <section id="skills" class="full-section">
      <div class="section-container">
        <div class="section-header">
          <span class="sub-tag">TECHNICAL EXPERTISE</span>
          <h2>Skills & Competencies</h2>
        </div>

        <div class="skills-wrapper">
          <div v-for="(group, index) in skills" :key="index" class="skill-panel">
            <div class="panel-top">
              <span class="panel-num">0{{ index + 1 }}</span>
              <h3>{{ group.title }}</h3>
            </div>
            <p class="panel-desc">{{ group.desc }}</p>
            <ul class="skill-list">
              <li v-for="(item, idx) in group.list" :key="idx">
                <span class="check-icon">✦</span> {{ item }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- PROJECTS SECTION -->
    <section id="projects" class="full-section alt-bg">
      <div class="section-container">
        <div class="section-header">
          <span class="sub-tag">PORTFOLIO SHOWCASE</span>
          <h2>Featured Projects (Image Gallery Slideshow)</h2>
        </div>

        <div class="project-showcase">
          <button @click="prevProject" class="proj-nav-btn left" aria-label="Previous Project">&#10094;</button>

          <div class="project-stage">
            <transition name="project-flip" mode="out-in">
              <div :key="currentProject" class="project-big-card">
                <div class="proj-left">
                  <span class="proj-big-num">{{ projects[currentProject].number }}</span>
                  <span class="proj-cat">{{ projects[currentProject].category }}</span>
                  <h3>{{ projects[currentProject].title }}</h3>
                  <p>{{ projects[currentProject].description }}</p>
                  <div class="proj-tags">
                    <span v-for="(t, i) in projects[currentProject].tech" :key="i" class="p-tag">
                      {{ t }}
                    </span>
                  </div>
                </div>
                <div class="proj-right">
                  <div class="project-img-container">
                    <img :src="projects[currentProject].image" :alt="projects[currentProject].title" class="proj-preview-img" />
                    <div class="proj-img-badge">Interactive App View</div>
                  </div>
                </div>
              </div>
            </transition>
          </div>

          <button @click="nextProject" class="proj-nav-btn right" aria-label="Next Project">&#10095;</button>
        </div>

        <div class="project-tabs">
          <button 
            v-for="(p, idx) in projects" 
            :key="idx" 
            class="tab-btn" 
            :class="{ active: currentProject === idx }"
            @click="currentProject = idx"
          >
            {{ p.number }}. {{ p.title }}
          </button>
        </div>
      </div>
    </section>

    <!-- FOOTER -->
    <footer id="contact" class="footer-full">
      <div class="section-container footer-content">
        <div class="footer-brand">
          <h2>MPANO<span>.JACKSON</span></h2>
          <p>L4 SOD Student at Collège de Bethel | Full-Stack Web Developer.</p>
        </div>
        <div class="footer-info">
          <p><strong>Education:</strong> Collège de Bethel (L4 SOD) • GS RUHANGO ADEPR</p>
          <p><strong>Tech Stack:</strong> Vue.js • CSS3 • Node.js • PHP • MySQL</p>
        </div>
      </div>
      <div class="footer-bottom">
        <p>&copy; 2026 MPANO Jabo Jackson. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<style>
:root {
  --bg-main: #090D16;
  --bg-secondary: #111827;
  --bg-card: #161F30;
  --emerald: #10B981;
  --emerald-dark: #059669;
  --emerald-glow: rgba(16, 185, 129, 0.25);
  --gold: #F59E0B;
  --gold-glow: rgba(245, 158, 11, 0.2);
  --text-light: #F9FAFB;
  --text-muted: #9CA3AF;
  --border-color: rgba(255, 255, 255, 0.08);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  scroll-behavior: smooth;
}

body {
  background-color: var(--bg-main);
  color: var(--text-light);
  font-family: 'Inter', 'Segoe UI', system-ui, sans-serif;
  line-height: 1.65;
  overflow-x: hidden;
  width: 100%;
}

.app-container {
  width: 100%;
  min-height: 100vh;
  position: relative;
}

.bg-glow {
  position: fixed;
  width: 500px;
  height: 500px;
  border-radius: 50%;
  filter: blur(130px);
  z-index: 0;
  pointer-events: none;
  animation: pulseGlow 8s ease-in-out infinite alternate;
}

.glow-1 { top: -150px; left: -100px; background: var(--emerald-glow); }
.glow-2 { bottom: -150px; right: -100px; background: var(--gold-glow); animation-delay: 4s; }

.navbar {
  position: sticky;
  top: 0;
  z-index: 100;
  width: 100%;
  background: rgba(9, 13, 22, 0.88);
  backdrop-filter: blur(14px);
  border-bottom: 1px solid var(--border-color);
}

.nav-inner {
  width: 92%;
  max-width: 1440px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
}

.brand {
  font-size: 1.6rem;
  font-weight: 800;
  letter-spacing: 1px;
  display: flex;
  align-items: center;
  gap: 10px;
}

.brand-dot {
  width: 12px;
  height: 12px;
  background: var(--emerald);
  border-radius: 50%;
  box-shadow: 0 0 12px var(--emerald);
}

.brand .accent { color: var(--emerald); }

.nav-menu {
  display: flex;
  align-items: center;
  list-style: none;
  gap: 32px;
}

.nav-menu a {
  color: var(--text-muted);
  text-decoration: none;
  font-weight: 500;
  font-size: 1rem;
  transition: color 0.3s;
}

.nav-menu a:hover { color: var(--emerald); }

.nav-cta {
  background: var(--emerald) !important;
  color: #052E16 !important;
  padding: 10px 22px;
  border-radius: 8px;
  font-weight: 700 !important;
  transition: transform 0.2s, background 0.3s !important;
}

.nav-cta:hover {
  background: #34D399 !important;
  transform: translateY(-2px);
}

.hero-fullscreen {
  position: relative;
  z-index: 1;
  width: 100%;
  min-height: calc(100vh - 82px);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  background: radial-gradient(circle at top right, rgba(16, 185, 129, 0.08), transparent 60%);
}

.hero-inner {
  width: 92%;
  max-width: 1440px;
  margin: auto;
  padding: 60px 0;
}

.hero-slide-grid {
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 50px;
  align-items: center;
}

.hero-slide-content { max-width: 800px; }

.hero-badge {
  display: inline-block;
  background: rgba(245, 158, 11, 0.12);
  color: var(--gold);
  border: 1px solid rgba(245, 158, 11, 0.35);
  padding: 8px 18px;
  border-radius: 30px;
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 1px;
  margin-bottom: 24px;
}

.hero-title {
  font-size: clamp(2.5rem, 4.5vw, 4.2rem);
  font-weight: 900;
  line-height: 1.1;
  margin-bottom: 14px;
  color: var(--text-light);
}

.hero-highlight {
  font-size: clamp(1.4rem, 2.5vw, 2.2rem);
  font-weight: 700;
  background: linear-gradient(90deg, var(--emerald), var(--gold));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 22px;
}

.hero-desc {
  font-size: 1.15rem;
  color: var(--text-muted);
  margin-bottom: 35px;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 18px;
  align-items: center;
}

.btn-emerald {
  background: var(--emerald);
  color: #052E16;
  padding: 16px 34px;
  border-radius: 10px;
  font-size: 1.05rem;
  font-weight: 700;
  text-decoration: none;
  box-shadow: 0 10px 25px rgba(16, 185, 129, 0.25);
  transition: all 0.3s ease;
  display: inline-block;
}

.btn-emerald:hover { background: #34D399; transform: translateY(-3px); }

.btn-outline {
  background: transparent;
  color: var(--text-light);
  border: 1.5px solid rgba(255, 255, 255, 0.2);
  padding: 16px 34px;
  border-radius: 10px;
  font-size: 1.05rem;
  font-weight: 600;
  text-decoration: none;
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  transition: all 0.3s ease;
}

.btn-outline:hover { border-color: var(--gold); color: var(--gold); transform: translateY(-3px); }

.hero-image-frame {
  position: relative;
  border-radius: 18px;
  overflow: hidden;
  border: 1px solid rgba(16, 185, 129, 0.3);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.5);
  height: 380px;
}

.hero-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.hero-image-frame:hover .hero-img { transform: scale(1.04); }

.img-badge-overlay {
  position: absolute;
  bottom: 15px;
  left: 15px;
  background: rgba(9, 13, 22, 0.85);
  backdrop-filter: blur(8px);
  padding: 8px 16px;
  border-radius: 8px;
  border: 1px solid var(--border-color);
  font-size: 0.9rem;
  font-weight: 700;
  color: var(--emerald);
}

.hero-controls {
  display: flex;
  align-items: center;
  gap: 20px;
  margin-top: 40px;
}

.arrow-btn {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  color: var(--text-light);
  font-size: 1.2rem;
  cursor: pointer;
  transition: all 0.3s;
}

.arrow-btn:hover { background: var(--emerald); color: #052E16; border-color: var(--emerald); }

.hero-indicators { display: flex; gap: 10px; }

.bar {
  width: 45px;
  height: 6px;
  background: rgba(255, 255, 255, 0.15);
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s;
}

.bar.active { background: var(--emerald); width: 70px; }

.stats-strip {
  width: 100%;
  background: var(--bg-secondary);
  border-top: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
  display: grid;
  grid-template-columns: repeat(4, 1fr);
}

.stat-item {
  padding: 28px 30px;
  border-right: 1px solid var(--border-color);
  text-align: center;
}

.stat-item:last-child { border-right: none; }

.stat-val {
  display: block;
  font-size: 1.35rem;
  font-weight: 800;
  color: var(--emerald);
  margin-bottom: 4px;
}

.stat-label { color: var(--text-muted); font-size: 0.9rem; }

.full-section {
  position: relative;
  z-index: 1;
  width: 100%;
  padding: 100px 0;
}

.alt-bg {
  background: var(--bg-secondary);
  border-top: 1px solid var(--border-color);
  border-bottom: 1px solid var(--border-color);
}

.section-container {
  width: 92%;
  max-width: 1440px;
  margin: 0 auto;
}

.section-header { margin-bottom: 55px; }

.sub-tag {
  display: inline-block;
  color: var(--gold);
  font-weight: 700;
  font-size: 0.9rem;
  letter-spacing: 1.5px;
  margin-bottom: 10px;
}

.section-header h2 { font-size: clamp(2rem, 3.5vw, 2.8rem); font-weight: 800; }

.about-grid {
  display: grid;
  grid-template-columns: 1.3fr 1fr;
  gap: 40px;
  align-items: start;
}

.about-text-card {
  background: var(--bg-card);
  padding: 40px;
  border-radius: 16px;
  border: 1px solid var(--border-color);
}

.about-text-card h3 { font-size: 1.8rem; margin-bottom: 18px; }
.text-emerald { color: var(--emerald); }
.about-text-card p { color: var(--text-muted); font-size: 1.08rem; margin-bottom: 18px; }

.terminal-box {
  margin-top: 25px;
  background: #06090F;
  border-radius: 12px;
  border: 1px solid rgba(16, 185, 129, 0.3);
  overflow: hidden;
}

.term-header {
  background: #0F1522;
  padding: 10px 16px;
  display: flex;
  align-items: center;
  gap: 8px;
}

.t-dot { width: 11px; height: 11px; border-radius: 50%; }
.t-dot.emerald { background: var(--emerald); }
.t-dot.gold { background: var(--gold); }
.t-dot.gray { background: #4B5563; }

.term-title { margin-left: 10px; font-size: 0.85rem; color: var(--text-muted); font-family: monospace; }
.terminal-box pre { padding: 18px; color: #34D399; font-family: 'Consolas', monospace; font-size: 0.95rem; overflow-x: auto; }

.services-column { display: flex; flex-direction: column; gap: 22px; }

.service-card {
  background: var(--bg-card);
  padding: 28px;
  border-radius: 16px;
  border: 1px solid var(--border-color);
  display: flex;
  gap: 20px;
  align-items: flex-start;
  transition: transform 0.3s, border-color 0.3s;
}

.service-card:hover { transform: translateX(8px); border-color: var(--emerald); }
.srv-icon { font-size: 2rem; background: rgba(16, 185, 129, 0.12); padding: 14px; border-radius: 12px; }
.service-card h4 { font-size: 1.25rem; margin-bottom: 6px; color: var(--text-light); }
.service-card p { color: var(--text-muted); font-size: 0.98rem; }

.edu-grid { display: grid; grid-template-columns: repeat(2, 1fr); gap: 35px; }

.edu-card {
  background: var(--bg-card);
  padding: 45px;
  border-radius: 18px;
  border: 1px solid var(--border-color);
  position: relative;
  transition: transform 0.3s;
}

.edu-card:hover { transform: translateY(-6px); }
.active-edu { border-top: 4px solid var(--emerald); }

.edu-badge {
  display: inline-block;
  background: rgba(16, 185, 129, 0.15);
  color: var(--emerald);
  padding: 6px 14px;
  border-radius: 6px;
  font-size: 0.85rem;
  font-weight: 700;
  margin-bottom: 18px;
}

.gold-badge { background: rgba(245, 158, 11, 0.15); color: var(--gold); }
.edu-card h3 { font-size: 1.9rem; margin-bottom: 8px; }
.edu-program { font-size: 1.15rem; color: var(--gold); font-weight: 600; margin-bottom: 16px; }
.edu-details { color: var(--text-muted); font-size: 1.05rem; }

.skills-wrapper { display: grid; grid-template-columns: repeat(3, 1fr); gap: 30px; }

.skill-panel {
  background: var(--bg-card);
  padding: 38px;
  border-radius: 18px;
  border: 1px solid var(--border-color);
  transition: border-color 0.3s, transform 0.3s;
}

.skill-panel:hover { border-color: var(--gold); transform: translateY(-5px); }
.panel-top { display: flex; align-items: center; gap: 15px; margin-bottom: 15px; }
.panel-num { font-size: 1.5rem; font-weight: 900; color: var(--emerald); }
.skill-panel h3 { font-size: 1.4rem; }
.panel-desc { color: var(--text-muted); margin-bottom: 22px; font-size: 0.98rem; }

.skill-list { list-style: none; display: flex; flex-direction: column; gap: 12px; }
.skill-list li {
  background: var(--bg-main);
  padding: 12px 16px;
  border-radius: 8px;
  font-weight: 500;
  border: 1px solid var(--border-color);
  display: flex;
  align-items: center;
  gap: 10px;
}

.check-icon { color: var(--gold); }

.project-showcase { display: flex; align-items: center; gap: 20px; width: 100%; }
.project-stage { width: 100%; }

.project-big-card {
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 20px;
  padding: 45px;
  display: grid;
  grid-template-columns: 1.2fr 1fr;
  gap: 40px;
  align-items: center;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.45);
}

.proj-big-num { display: block; font-size: 3.5rem; font-weight: 900; color: rgba(16, 185, 129, 0.2); line-height: 1; margin-bottom: 10px; }
.proj-cat { color: var(--gold); font-weight: 700; text-transform: uppercase; font-size: 0.9rem; letter-spacing: 1px; }
.proj-left h3 { font-size: 2.1rem; margin: 10px 0 18px; }
.proj-left p { color: var(--text-muted); font-size: 1.08rem; margin-bottom: 25px; }

.proj-tags { display: flex; flex-wrap: wrap; gap: 10px; }
.p-tag { background: rgba(16, 185, 129, 0.14); color: var(--emerald); padding: 7px 16px; border-radius: 20px; font-size: 0.9rem; font-weight: 600; }

.project-img-container {
  position: relative;
  border-radius: 14px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.15);
  height: 280px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.4);
}

.proj-preview-img { width: 100%; height: 100%; object-fit: cover; transition: transform 0.4s ease; }
.project-img-container:hover .proj-preview-img { transform: scale(1.05); }

.proj-img-badge {
  position: absolute;
  top: 12px;
  right: 12px;
  background: rgba(16, 185, 129, 0.9);
  color: #052E16;
  padding: 5px 12px;
  border-radius: 6px;
  font-weight: 700;
  font-size: 0.8rem;
}

.proj-nav-btn {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  color: var(--text-light);
  font-size: 1.4rem;
  cursor: pointer;
  flex-shrink: 0;
  transition: all 0.3s;
}

.proj-nav-btn:hover { background: var(--gold); color: #090D16; }

.project-tabs { display: flex; flex-wrap: wrap; justify-content: center; gap: 14px; margin-top: 35px; }

.tab-btn {
  background: var(--bg-card);
  color: var(--text-muted);
  border: 1px solid var(--border-color);
  padding: 12px 20px;
  border-radius: 10px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s;
}

.tab-btn.active, .tab-btn:hover {
  border-color: var(--emerald);
  color: var(--emerald);
  background: rgba(16, 185, 129, 0.1);
}

.footer-full { background: #06090F; border-top: 1px solid var(--border-color); padding-top: 60px; }
.footer-content { display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 30px; padding-bottom: 40px; }
.footer-brand h2 { font-size: 1.8rem; margin-bottom: 8px; }
.footer-brand span { color: var(--emerald); }
.footer-brand p, .footer-info p { color: var(--text-muted); }
.footer-bottom { text-align: center; padding: 25px; border-top: 1px solid var(--border-color); color: #6B7280; font-size: 0.95rem; }

.hero-slide-enter-active, .hero-slide-leave-active { transition: all 0.5s cubic-bezier(0.25, 0.8, 0.25, 1); }
.hero-slide-enter-from { opacity: 0; transform: translateY(25px); }
.hero-slide-leave-to { opacity: 0; transform: translateY(-25px); }

.project-flip-enter-active, .project-flip-leave-active { transition: all 0.45s ease; }
.project-flip-enter-from { opacity: 0; transform: scale(0.96) translateX(30px); }
.project-flip-leave-to { opacity: 0; transform: scale(0.96) translateX(-30px); }

@keyframes pulseGlow {
  0% { transform: scale(1); opacity: 0.6; }
  100% { transform: scale(1.2); opacity: 1; }
}

@media (max-width: 1024px) {
  .about-grid, .project-big-card, .skills-wrapper, .hero-slide-grid { grid-template-columns: 1fr; }
  .stats-strip { grid-template-columns: repeat(2, 1fr); }
}

@media (max-width: 768px) {
  .nav-menu { display: none; }
  .edu-grid, .stats-strip { grid-template-columns: 1fr; }
  .project-big-card { padding: 30px; }
}
</style>
<template>
  <main>

    <!-- HERO -->
    <section id="home" class="hero">
      <div class="hero-content">
        <div class="hero-text">
          <p class="hero-tag">👋 Welcome to my portfolio</p>
          <h1>Hi, I'm <span class="accent">Ta Sbo</span></h1>
          <p class="subtitle">EdTech Developer & Learning Experience Designer crafting digital tools that help learners thrive.</p>
          <div class="hero-btns">
            <a href="#projects" class="btn">View My Work</a>
            <a href="#contact" class="btn btn-outline">Contact Me</a>
          </div>
        </div>
        <div class="hero-image">
          <div class="image-ring">
            <img src="/images/profile.png" alt="Ta Sbo" />
          </div>
        </div>
      </div>
      <div class="hero-wave">
        <svg viewBox="0 0 1440 80" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
          <path d="M0,40 C360,80 1080,0 1440,40 L1440,80 L0,80 Z" fill="var(--bg)"/>
        </svg>
      </div>
    </section>

    <!-- ABOUT -->
    <section id="about" class="section">
      <div class="section-header">
        <span class="section-tag">About</span>
        <h2>Who I Am</h2>
      </div>
      <div class="about-grid">
        <div class="about-card">
          <span class="about-icon">🎯</span>
          <h3>My Mission</h3>
          <p>Building digital learning experiences that are engaging, accessible, and effective for every learner.</p>
        </div>
        <div class="about-card">
          <span class="about-icon">🌍</span>
          <h3>My Background</h3>
          <p>I combine education expertise with modern web development to create tools that make a real difference.</p>
        </div>
        <div class="about-card">
          <span class="about-icon">🚀</span>
          <h3>My Goal</h3>
          <p>To bridge the gap between technology and education, making quality learning accessible to all.</p>
        </div>
      </div>
    </section>

    <!-- PROJECTS -->
    <section id="projects" class="section alt">
      <div class="section-header">
        <span class="section-tag">Work</span>
        <h2>Featured Projects</h2>
      </div>
      <div class="grid">
        <div v-for="project in projects" :key="project.id" class="card">
          <div class="card-accent"></div>
          <div class="card-body">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
            <div class="tags">
              <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
            <div class="card-links">
              <a v-if="project.githubUrl" :href="project.githubUrl" target="_blank" class="card-btn">
                GitHub →
              </a>
              <a v-if="project.liveUrl" :href="project.liveUrl" target="_blank" class="card-btn card-btn-primary">
                Live Demo →
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- SKILLS -->
    <section id="skills" class="section">
      <div class="section-header">
        <span class="section-tag">Skills</span>
        <h2>What I Do</h2>
      </div>
      <div class="skills-grid">
        <div v-for="skill in skills" :key="skill.name" class="skill-card">
          <div class="skill-icon-wrap">
            <span class="skill-icon">{{ skill.icon }}</span>
          </div>
          <h3>{{ skill.name }}</h3>
          <p>{{ skill.description }}</p>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" class="section contact-section">
      <div class="contact-box">
        <span class="section-tag">Contact</span>
        <h2>Let's Work Together</h2>
        <p>Have a project in mind or want to collaborate? I'd love to hear from you!</p>
        <a href="mailto:your@email.com" class="btn">Send Me an Email</a>
      </div>
    </section>

  </main>
</template>

<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    id: 1,
    title: 'Interactive Math Quiz App',
    description: 'A gamified quiz platform for Grade 4–6 learners with instant feedback and progress tracking.',
    tags: ['Vue', 'Education', 'Gamification'],
    githubUrl: 'https://github.com/elignobis',
    liveUrl: ''
  },
  {
    id: 2,
    title: 'Teacher Dashboard',
    description: 'Analytics dashboard for tracking student progress, engagement and learning outcomes.',
    tags: ['Vue', 'Charts', 'UX Design'],
    githubUrl: 'https://github.com/elignobis',
    liveUrl: ''
  },
  {
    id: 3,
    title: 'Online Learning Portal',
    description: 'A full LMS with course management, video lessons and student assessments.',
    tags: ['Vue', 'LMS', 'EdTech'],
    githubUrl: 'https://github.com/elignobis',
    liveUrl: ''
  }
])

const skills = ref([
  { icon: '🎨', name: 'UI/UX Design', description: 'Intuitive learning experiences' },
  { icon: '💻', name: 'Vue.js', description: 'Interactive web apps' },
  { icon: '📚', name: 'Curriculum Design', description: 'Effective learning paths' },
  { icon: '🛠️', name: 'EdTech Tools', description: 'LMS & authoring tools' },
  { icon: '📊', name: 'Analytics', description: 'Tracking learner outcomes' },
  { icon: '🤝', name: 'Collaboration', description: 'Educators & developers' },
])
</script>

<style scoped>
/* Hero */
.hero {
  background: linear-gradient(135deg, rgb(30,41,59) 0%, #334c83 50%, #3c63a3 100%);
  padding: 5rem 3rem 0;
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -20%;
  width: 600px;
  height: 600px;
  background: rgba(255,255,255,0.05);
  border-radius: 50%;
}

.hero-content {
  max-width: 960px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 3rem;
  padding-bottom: 5rem;
}

.hero-text { flex: 1; }

.hero-tag {
  display: inline-block;
  background: rgba(255,255,255,0.15);
  color: white;
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  margin-bottom: 1.5rem;
  backdrop-filter: blur(10px);
}

.hero h1 {
  font-size: clamp(2.2rem, 5vw, 3.5rem);
  color: white;
  line-height: 1.2;
  margin-bottom: 1rem;
}

.accent {
  background: linear-gradient(90deg, #bfdbfe, #ffffff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle {
  color: rgba(255,255,255,0.85);
  font-size: clamp(1rem, 2vw, 1.15rem);
  line-height: 1.8;
  margin-bottom: 2rem;
  max-width: 480px;
}

.hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; }

.btn {
  background: white;
  color: #84a1e1;
  padding: 0.75rem 2rem;
  border-radius: 8px;
  text-decoration: none;
  font-weight: 700;
  display: inline-block;
  transition: all 0.2s;
  font-size: 0.95rem;
}

.btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.2);
}

.btn-outline {
  background: transparent;
  color: white;
  border: 2px solid rgba(255,255,255,0.6);
}

.btn-outline:hover {
  background: rgba(255,255,255,0.1);
  border-color: white;
}

/* Profile image */
.hero-image { flex-shrink: 0; }

.image-ring {
  width: 280px;
  height: 280px;
  border-radius: 50%;
  padding: 5px;
  background: linear-gradient(135deg, rgba(255,255,255,0.5), rgba(255,255,255,0.1));
  box-shadow: 0 20px 60px rgba(0,0,0,0.3);
}

.image-ring img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  object-fit: cover;
  display: block;
}

/* Wave */
.hero-wave {
  position: relative;
  bottom: -1px;
  line-height: 0;
}

.hero-wave svg { width: 100%; display: block; }

/* Section styles */
.section {
  padding: 5rem 2rem;
  max-width: 960px;
  margin: 0 auto;
  text-align: center;
}

.section.alt {
  background: var(--bg-alt);
  max-width: 100%;
  padding: 5rem 2rem;
}

.section.alt > * {
  max-width: 960px;
  margin-left: auto;
  margin-right: auto;
}

.section-header {
  margin-bottom: 3rem;
}

.section-tag {
  display: inline-block;
  background: linear-gradient(135deg, #eff6ff, #dbeafe);
  color: #2563eb;
  padding: 0.3rem 1rem;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
}

.dark .section-tag {
  background: rgba(59,130,246,0.2);
  color: #93c5fd;
}

h2 {
  font-size: clamp(1.8rem, 4vw, 2.5rem);
  color: var(--text);
  margin: 0;
}

/* About cards */
.about-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 1.5rem;
  text-align: left;
}

.about-card {
  background: var(--surface);
  border-radius: 16px;
  padding: 2rem;
  border: 1px solid var(--border);
  box-shadow: 0 4px 20px var(--shadow);
  transition: transform 0.2s;
}

.about-card:hover { transform: translateY(-4px); }

.about-icon { font-size: 2rem; display: block; margin-bottom: 1rem; }

.about-card h3 {
  color: var(--text);
  margin-bottom: 0.5rem;
  font-size: 1.1rem;
}

.about-card p { color: var(--text-muted); line-height: 1.7; font-size: 0.95rem; }

/* Project cards */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  text-align: left;
}

.card {
  background: var(--surface);
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 4px 20px var(--shadow);
  border: 1px solid var(--border);
  transition: transform 0.2s, box-shadow 0.2s;
}

.card:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 40px var(--shadow);
}

.card-accent {
  height: 5px;
  background: linear-gradient(90deg, #2563eb, #3b82f6, #60a5fa);
}

.card-body { padding: 1.5rem; }

.card-body h3 { color: var(--text); margin-bottom: 0.5rem; font-size: 1.1rem; }
.card-body p { color: var(--text-muted); font-size: 0.9rem; margin-bottom: 1rem; line-height: 1.6; }

.tags { display: flex; flex-wrap: wrap; gap: 0.5rem; margin-bottom: 1.25rem; }

.tag {
  background: var(--bg-alt);
  color: var(--primary);
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 500;
}

.card-links { display: flex; gap: 0.75rem; }

.card-btn {
  text-decoration: none;
  font-size: 0.875rem;
  font-weight: 600;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  border: 1px solid var(--border);
  color: var(--text);
  transition: all 0.2s;
}

.card-btn:hover { background: var(--bg-alt); }

.card-btn-primary {
  background: var(--primary);
  color: white;
  border-color: var(--primary);
}

.card-btn-primary:hover { background: var(--primary-hover); }

/* Skills */
.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1rem;
}

.skill-card {
  background: var(--surface);
  border-radius: 16px;
  padding: 1.5rem 1rem;
  text-align: center;
  box-shadow: 0 4px 20px var(--shadow);
  border: 1px solid var(--border);
  transition: transform 0.2s, box-shadow 0.2s;
}

.skill-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 30px var(--shadow);
}

.skill-icon-wrap {
  width: 56px;
  height: 56px;
  background: linear-gradient(135deg, #eff6ff, #dbeafe);
  border-radius: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1rem;
}

.dark .skill-icon-wrap { background: rgba(59,130,246,0.15); }

.skill-icon { font-size: 1.75rem; }
.skill-card h3 { font-size: 0.95rem; margin-bottom: 0.25rem; color: var(--text); font-weight: 600; }
.skill-card p { font-size: 0.8rem; color: var(--text-muted); }

/* Contact */
.contact-section {
  max-width: 100% !important;
  background: linear-gradient(135deg, #1e40af 0%, #2563eb 100%);
  padding: 5rem 2rem !important;
}

.contact-box {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.contact-section .section-tag {
  background: rgba(255,255,255,0.2);
  color: white;
}

.contact-section h2 {
  color: white;
  margin-bottom: 1rem;
}

.contact-section p {
  color: rgba(255,255,255,0.85);
  margin-bottom: 2rem;
  line-height: 1.7;
}

.contact-section .btn {
  background: white;
  color: #2563eb;
  font-weight: 700;
}

/* Mobile */
@media (max-width: 768px) {
  .hero { padding: 3rem 1.5rem 0; }
  .hero-content {
    flex-direction: column-reverse;
    text-align: center;
    padding-bottom: 4rem;
    gap: 2rem;
  }
  .subtitle { margin: 0 auto 2rem; }
  .hero-btns { justify-content: center; }
  .image-ring { width: 200px; height: 200px; }
  .section { padding: 3rem 1.5rem; }
  .grid { grid-template-columns: 1fr; }
  .skills-grid { grid-template-columns: repeat(2, 1fr); }
  .about-grid { grid-template-columns: 1fr; }
}
</style>
<template>
  <main>

    <!-- HERO -->
    <section id="home" style="padding: 6rem 2rem; text-align: center; background: #f0f9ff;">
      <h1 style="font-size: 3rem; margin-bottom: 1rem;">Hi, I'm <span style="color: #2563eb;">Sibongile</span> 👋</h1>
      <p style="font-size: 1.25rem; color: #64748b; margin-bottom: 2rem;">EdTech Developer & Learning Experience Designer</p>
      <a href="#projects" style="background: #2563eb; color: white; padding: 0.75rem 2rem; border-radius: 8px; text-decoration: none; font-weight: 600;">View My Work</a>
    </section>

    <!-- ABOUT -->
    <section id="about" style="padding: 4rem 2rem; max-width: 700px; margin: 0 auto; text-align: center;">
      <h2 style="font-size: 2rem; margin-bottom: 1rem;">About Me</h2>
      <p style="color: #64748b; line-height: 1.8;">I am passionate about building digital learning experiences that are engaging, accessible, and effective. I combine education expertise with modern web development to create tools that help learners thrive.</p>
    </section>

    <!-- PROJECTS -->
    <section id="projects" style="padding: 4rem 2rem; background: #f8fafc;">
      <h2 style="font-size: 2rem; text-align: center; margin-bottom: 2rem;">Projects</h2>
      <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem; max-width: 900px; margin: 0 auto;">
        <div v-for="project in projects" :key="project.id" style="background: white; border-radius: 12px; padding: 1.5rem; box-shadow: 0 4px 20px rgba(0,0,0,0.08);">
          <h3 style="margin-bottom: 0.5rem;">{{ project.title }}</h3>
          <p style="color: #64748b; font-size: 0.9rem; margin-bottom: 1rem;">{{ project.description }}</p>
          <div style="display: flex; gap: 0.5rem; flex-wrap: wrap; margin-bottom: 1rem;">
            <span v-for="tag in project.tags" :key="tag" style="background: #eff6ff; color: #2563eb; padding: 0.2rem 0.6rem; border-radius: 20px; font-size: 0.8rem;">{{ tag }}</span>
          </div>
          <a v-if="project.githubUrl" :href="project.githubUrl" target="_blank" style="color: #2563eb; font-size: 0.9rem; margin-right: 1rem;">GitHub →</a>
          <a v-if="project.liveUrl" :href="project.liveUrl" target="_blank" style="color: #2563eb; font-size: 0.9rem;">Live Demo →</a>
        </div>
      </div>
    </section>

    <!-- SKILLS -->
    <section id="skills" style="padding: 4rem 2rem;">
      <h2 style="font-size: 2rem; text-align: center; margin-bottom: 2rem;">Skills</h2>
      <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 1rem; max-width: 800px; margin: 0 auto;">
        <div v-for="skill in skills" :key="skill.name" style="background: white; border-radius: 12px; padding: 1.25rem; text-align: center; box-shadow: 0 4px 20px rgba(0,0,0,0.06);">
          <div style="font-size: 2rem;">{{ skill.icon }}</div>
          <h3 style="font-size: 1rem; margin: 0.5rem 0;">{{ skill.name }}</h3>
          <p style="font-size: 0.8rem; color: #64748b;">{{ skill.description }}</p>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact" style="padding: 4rem 2rem; background: #f8fafc; text-align: center;">
      <h2 style="font-size: 2rem; margin-bottom: 1rem;">Get In Touch</h2>
      <p style="color: #64748b; margin-bottom: 2rem;">Interested in working together? Let's connect!</p>
      <a href="mailto:your@email.com" style="background: #2563eb; color: white; padding: 0.75rem 2rem; border-radius: 8px; text-decoration: none; font-weight: 600;">Email Me</a>
    </section>

  </main>
</template>

<script setup>
import { ref } from 'vue'

const projects = ref([
  {
    id: 1,
    title: 'Interactive Math Quiz App',
    description: 'A gamified quiz platform for Grade 4–6 learners with instant feedback.',
    tags: ['Vue', 'Education', 'Gamification'],
    githubUrl: 'https://github.com/elignobis',
    liveUrl: ''
  },
  {
    id: 2,
    title: 'Teacher Dashboard',
    description: 'Analytics dashboard for tracking student progress and engagement.',
    tags: ['Vue', 'Charts', 'UX Design'],
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
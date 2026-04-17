<template>
  <section id="projects">
    <h2>Projects</h2>
    <div class="grid">
      <div v-for="project in projects" :key="project.id" class="card">
        <img :src="project.image" :alt="project.title" />
        <h3>{{ project.title }}</h3>
        <p>{{ project.description }}</p>
        <div class="tags">
          <span v-for="tag in project.tags" :key="tag">{{ tag }}</span>
        </div>
        <a :href="project.githubUrl" target="_blank">GitHub</a>
        <a v-if="project.liveUrl" :href="project.liveUrl" target="_blank">Live Demo</a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { projects } from '../data/projects.js'
</script>
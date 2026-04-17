<template>
  <section id="skills">
    <h2>Skills & Tools</h2>
    <div class="skills-grid">
      <div class="skill-card" v-for="skill in skills" :key="skill.name">
        <span class="skill-icon">{{ skill.icon }}</span>
        <h3>{{ skill.name }}</h3>
        <p>{{ skill.description }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = [
  { icon: '🎨', name: 'UI/UX Design', description: 'Designing intuitive learning experiences' },
  { icon: '💻', name: 'Vue.js', description: 'Building interactive web applications' },
  { icon: '📚', name: 'Curriculum Design', description: 'Structuring effective learning paths' },
  { icon: '🛠️', name: 'EdTech Tools', description: 'LMS platforms and authoring tools' },
  { icon: '📊', name: 'Data & Analytics', description: 'Tracking learner progress and outcomes' },
  { icon: '🤝', name: 'Collaboration', description: 'Working with educators and developers' },
]
</script>

<style scoped>
#skills {
  padding: 4rem 2rem;
  text-align: center;
}

h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  max-width: 900px;
  margin: 0 auto;
}

.skill-card {
  background: white;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
  transition: transform 0.2s;
}

.skill-card:hover {
  transform: translateY(-4px);
}

.skill-icon {
  font-size: 2.5rem;
}

h3 {
  margin: 0.75rem 0 0.5rem;
  font-size: 1rem;
}

p {
  font-size: 0.875rem;
  color: #64748b;
}
</style>
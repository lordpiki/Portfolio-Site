<template>
  <div>
    <div class="container">
      <div class="header">
        <h1>Hello, I'm Miki</h1>
        <p>Welcome to my portfolio</p>
      </div>

      <!-- Navigation Bar -->
      <div class="navigation-bar">
        <div class="button-container">
          <button :class="{ 'selected': currentSection === 'welcome' }" @click="showSection('welcome')">Welcome</button>
        </div >
        <div class="button-container">
          <button :class="{ 'selected': currentSection === 'projects' }" @click="showSection('projects')">Projects</button>
        </div>
        <div class="button-container">
          <button :class="{ 'selected': currentSection === 'contact' }" @click="showSection('contact')">Contact</button>
        </div>
      </div>

      <!-- Content Sections -->
      <div v-if="currentSection === 'welcome'" id="welcome">
        <h2>Welcome Section</h2>
        <!-- Add your welcome content here -->
      </div>

      <div v-if="currentSection === 'projects'" id="projects">
        <!-- Projects Showcase -->
        <div class="projects">
          <div v-for="project in projects" :key="project.id" class="project-card">
            <h3>{{ project.name }}</h3>
            <p>{{ project.description }}</p>
            <!-- Add more project details as needed -->
          </div>
        </div>
      </div>

      <div v-if="currentSection === 'contact'" id="contact" class="contact">
        <h2>Contact Me</h2>
        <p>Email: <a href="mailto:your.email@example.com">your.email@example.com</a></p>
        <p>LinkedIn: <a href="https://www.linkedin.com/in/your-linkedin-profile/">LinkedIn Profile</a></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentSection: 'welcome',
      projects: [
        { id: 1, name: 'Project 1', description: 'Description 1' },
        { id: 2, name: 'Project 2', description: 'Description 2' },
        // Add more projects
      ],
    };
  },
  methods: {
    showSection(section) {
      this.currentSection = section;
    },
  },
};
</script>

<style src="../styles/PageIndex.css"></style>

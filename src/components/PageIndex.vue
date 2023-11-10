<template>
  <div>
    <div class="container">
      <div class="header">
        <h1>Hello, I'm Miki</h1>
        <p>Welcome to my portfolio</p>
      </div>

      <!-- Projects Showcase -->
      <div class="projects">
        <div v-for="project in projects" :key="project.id" class="project-card">
          <h3>{{ project.name }}</h3>
          <p>{{ project.description }}</p>
          <!-- Add more project details as needed -->
        </div>
      </div>

      <!-- Contact Section -->
      <div class="contact">
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
      projects: [
        { id: 1, name: 'Project 1', description: 'Description 1' },
        { id: 2, name: 'Project 2', description: 'Description 2' },
        // Add more projects
      ],
    };
  },
};
</script>

<style src="../styles/PageIndex.css"></style>
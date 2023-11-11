<template>
  <div>
    <div class="container">
      <div class="header">
        <h1>Hello, I'm Miki</h1>
        <p>Welcome to my portfolio</p>
      </div>

      <div class="navigation-bar">
        <button @click="scrollToSection('welcome')">Welcome</button>
        <button @click="scrollToSection('projects')">Projects</button>
        <button @click="scrollToSection('contact')">Contact</button>
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
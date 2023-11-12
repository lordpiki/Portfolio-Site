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
          <div v-for="project in projects" :key="project.id" class="project-card" >
            <img :src="require(`../assets/${project.image}`)" alt="Project Image" @click="goToProject(project.id)">
            <h3>{{ project.name }}</h3>
            <p>{{ project.description }}</p>
            <div class="repos">
              <div class="project-repo" v-if="project.Github" @click="goToRepo(project.id)">
                <Github />
              </div>
              <div class="project-repo" v-if="project.Gitlab" @click="goToRepo(project.id)">
                <Gitlab />
              </div>
            </div>
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
import axios from 'axios';

import { Github, Gitlab } from 'lucide-vue-next';

export default {
  components: {
    Github,
    Gitlab,
  },
  data() {
    return {
      currentSection: 'welcome',
      projects: [],
    };
  },
  methods: {
    async loadProjects() {
      try {
        const response = await axios.get('projects.json'); // Adjust the path accordingly
        this.projects = response.data;
      } catch (error) {
        console.error('Error loading projects:', error);
      }
    },
    showSection(section) {
      this.loadProjects();
      this.currentSection = section;
    },
    goToProject(projectId) {
      const project = this.projects.find(proj => proj.id === projectId);
      if (project && project.link) {
        window.open(project.link, '_blank');
      } else {
        console.error(`Project with ID ${projectId} does not have a valid link.`);
      }
    },
    goToRepo(projectId) {
      const project = this.projects.find(proj => proj.id === projectId);
      if (project && project.repo_link) {
        window.open(project.repo_link, '_blank');
      } else {
        console.error(`Project with ID ${projectId} does not have a valid link.`);
      }
    }
  },
};
</script>

<style src="../styles/PageIndex.css"></style>

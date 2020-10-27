<template>
  <v-container class="grey lighten-5" v-if="dataLoaded" fluid>
    <v-row>
      <v-col
        v-for="project in projects" :key="project.id"
        md="4"
        sm="6"
        align-self="center"
      >
        <ProjectCard 
          :project="project"
        />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import ProjectCard from './ProjectCard';

export default {
  name: 'ProjectsGrid',

  components: {
    ProjectCard,
  },

  data: () => ({
    projects: [
      {
        description: "SPA",
        id: 5,
        main_technology: "Vue",
        name: "Frontend этого сайта",
        source_code_link: "https://github.com/komproma1z/portfolio_frontend",
        technologies_used: "Vue, Vuetify",
        url: "no",
      },
      {
        description: "REST API",
        id: 6,
        main_technology: "Node",
        name: "Backend этого сайта",
        source_code_link: "https://github.com/komproma1z/portfolio_backend",
        technologies_used: "Node, Firebase",
        url: "https://kmz-portfolio-api.herokuapp.com/data",
      }
    ],
    dataLoaded: false,
  }),
  methods: {
    fetchData: function() {
      fetch("https://kmz-portfolio-api.herokuapp.com/data")
        .then(res => res.json())
        .then(data => {
          this.projects = [...Object.values(data["data"]["sites"]), ...this.projects];
          this.dataLoaded = true;
        })
      .catch(err => err);
    },
  },
  created() {
    this.fetchData();
  },
};
</script>
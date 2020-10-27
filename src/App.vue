<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <h2>Alexey Kanin</h2>
        <subtitle-1 style="margin-left: 5px">portfolio</subtitle-1>
      </div>
    </v-app-bar>

    <v-main>
      <ProjectsGrid/>
    </v-main>
  </v-app>
</template>

<script>
import ProjectsGrid from './components/ProjectsGrid';

export default {
  name: 'App',

  components: {
    ProjectsGrid,
  },
  mounted: function() {
    let elHtml = document.getElementsByTagName('html')[0]
    elHtml.style.overflowY = 'auto'
  },
  destroyed: function() {
    let elHtml = document.getElementsByTagName('html')[0]
    elHtml.style.overflowY = null
  }
};
</script>

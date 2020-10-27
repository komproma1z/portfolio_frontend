<template>
  <v-card
    class="mx-auto"
    max-width="400"
    outlined
  >
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">
          {{project.main_technology}}
        </div>
        <v-list-item-title class="headline mb-1">
          {{project.name}}
        </v-list-item-title>
        <v-list-item-subtitle class="font-weight-bold">Описание:</v-list-item-subtitle>
        <v-list-item-subtitle style="margin-bottom: 15px">{{project.description}}</v-list-item-subtitle>
        <v-list-item-subtitle class="font-weight-bold">Использованные технологии:</v-list-item-subtitle>
        <v-list-item-subtitle>{{project.technologies_used}}</v-list-item-subtitle>
      </v-list-item-content>

      <v-list-item-avatar
        tile
        size="100"
      >
      <v-img
        max-height="150"
        max-width="250"
        :src="require(`@/assets/${project.main_technology.toLowerCase()}.png`)"
      ></v-img>
      </v-list-item-avatar>
    </v-list-item>

    <v-card-actions>
      <v-btn 
        v-on:click="directToUrl(project.url)" 
        outlined 
        rounded 
        text 
        small 
        :disabled="project.url === 'no' ? true : false" 
        style="margin-right: 10px">
        На сайт
      </v-btn>
      <v-btn 
        outlined 
        rounded 
        text 
        small
        v-on:click="directToUrl(project.source_code_link)">
        Репозиторий
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "ProjectCard",
  props: ["project"],
  methods: {
    directToUrl: function(url) {
      window.open(url);
    }
  }
}
</script>
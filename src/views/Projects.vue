<template>
  <div class="projects">
    <h1 class="subheading grey--text">Projects</h1>

    <v-container class="my-5">
      <v-expansion-panel>
        <v-expansion-panel-content v-for="project in myProjects" :key="project.id">
          <div slot="header">{{ project.name}}</div>
          <v-card>
            <v-card-text class="px-4 grey--text">
              <div class="font-weight-bold">{{project.due_date}}</div>
              <div>{{project.description}}</div>
            </v-card-text>
          </v-card>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-container>    

  </div>
</template>

<script>
import axios from 'axios'

export default {
  mounted(){
    axios.get('http://192.168.0.9:8000/projects/projects/')
    .then( (res) => {
      this.projects = res.data
    })
  },
  data(){
    return{
      projects:[
      ]
    }
  },
  computed: {
    myProjects(){
      return this.projects.filter(project => {
        return project.leader.name === 'Jose Roberto Estupinián'
      })
    }
  }

}
</script>

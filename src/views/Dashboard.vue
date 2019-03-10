<template>
  <div class="dashboard">
    <h1>Dashboard</h1>
    <v-container class="my-5">

      <v-layout row class="mb-3">
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('title')" slot="activator">
            <v-icon left small>folder</v-icon>
            <span class="caption text-lowercase">By project name</span>
          </v-btn>
          <span>Sort the projects by project name</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
            <v-icon left small>person</v-icon>
            <span class="caption text-lowercase">By person</span>
          </v-btn>
          <span>Sort the projects by person name</span>
        </v-tooltip>
        <v-tooltip top>
          <v-btn small flat color="grey" @click="sortBy('due')" slot="activator">
            <v-icon left small>calendar_today</v-icon>
            <span class="caption text-lowercase">By Due Date</span>
          </v-btn>
          <span>Sort the projects by due Date</span>
        </v-tooltip>

      </v-layout>

      <v-card flat v-for="project in projects" :key="project.id">
        <v-layout row wrap :class="`pa-3 project ${project.project_status}`">
          <v-flex xs12 md6 >
            <div class="caption grey--text">Project title</div>
            <div>{{ project.name }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Person</div>
            <div>{{ project.leader.name }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Due by</div>
            <div>{{ project.due_date }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="right">
              <v-chip small :class="`${project.project_status} white--text caption my-2`">{{ project.project_status }}</v-chip>
            </div>
          </v-flex>
        </v-layout>
        <v-divider></v-divider>
      </v-card>

    </v-container>        

  </div>
</template>

<script>
import axios from 'axios'

export default {
  mounted(){
    // function getProjects(){
    //   return axios.get('http://192.168.0.9:8000/projects/projects/')
    // }
    // function getLeader(){
    //   return axios.get('')

    // }
    axios.get('http://192.168.0.9:8000/projects/projects/').then( (res) => {
      this.projects=res.data
    })
  },
  data() {
    return {
      projects:[
      ],
      leader:[]
      
    }
  },
  methods:{
    sortBy(prop){
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
}
</script>

<style>
.project.Idea {
  border-left: 4px solid khaki;
}
.project.Requested {
  border-left: 4px solid khaki;
}
.project.Approved {
  border-left: 4px solid cadetblue;
}
.project.Rejected {
  border-left: 4px solid grey;
}
.project.Planning {
  border-left: 4px solid blue;
}
.project.Ongoing {
  border-left: 4px solid darkgreen;
}
.project.Dead {
  border-left: 4px solid black;
}
.project.On_hold {
  border-left: 4px solid darkorange;
}

.project.Complete {
  border-left: 4px solid darkgray;
}
.project.Overdue {
  border-left: 4px solid darkred;
}

.v-chip.Idea{
  background: khaki;
}

.v-chip.Requested{
  background: khaki;
}

.v-chip.Approved{
  background: cadetblue;
}

.v-chip.Rejected{
  background: grey;
}

.v-chip.Planning{
  background: blue;
}

.v-chip.Ongoing{
  background: darkgreen;
}

.v-chip.Dead{
  background: black;
}

.v-chip.On_hold{
  background: darkorange;
}

.v-chip.Complete{
  background: darkgray;
}

.v-chip.Overdue{
  background: darkred;
}

</style>

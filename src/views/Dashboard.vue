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

      <v-card flat v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6 >
            <div class="caption grey--text">Project title</div>
            <div>{{ project.title }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Person</div>
            <div>{{ project.person }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Due by</div>
            <div>{{ project.due }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="right">
              <v-chip small :class="`${project.status} white--text caption my-2`">{{ project.status }}</v-chip>
            </div>
          </v-flex>
        </v-layout>
        <v-divider></v-divider>
      </v-card>

    </v-container>        

  </div>
</template>

<script>


export default {
  data() {
    return {
      projects:[
        {title: 'Auditoría de Ventas, Ingresos', person:'Jose Roberto', due:'2019.03.20', status:'ongoing', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.' },
        {title: 'Auditoría de Ventas, Ingresos Carga', person:'Carolina Delgado', due:'2019.03.25', status:'ongoing', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.'},
        {title: 'Auditoría de Planificación de Inventarios', person:'Luz Dary Puerto', due:'2019.04.01', status:'completed', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.'},
        {title: 'Auditoría de flota O6', person:'Jhon Caballero', due:'2019.02.31', status:'overdue', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.'}
      ]
      
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
.project.completed {
  border-left: 4px solid #3cd1c2;
}
.project.ongoing {
  border-left: 4px solid orange;
}
.project.overdue {
  border-left: 4px solid tomato;
}

.v-chip.completed{
  background: #3cd1c2;
}

.v-chip.ongoing{
  background: orange;
}

.v-chip.overdue{
  background: tomato;
}
</style>

<template>
  <div class="projects">
    <h1 class="subheading grey--text">Projects</h1>

    <v-container class="my-5">
      <v-expansion-panel>
        <v-expansion-panel-content v-for="project in myProjects" :key="project.title">
          <div slot="header">{{ project.title}}</div>
          <v-card>
            <v-card-text class="px-4 grey--text">
              <div class="font-weight-bold">{{project.due}}</div>
              <div>{{project.content}}</div>
            </v-card-text>
          </v-card>
        </v-expansion-panel-content>
      </v-expansion-panel>
    </v-container>    

  </div>
</template>

<script>


export default {
  data(){
    return{
      projects:[
        {title: 'Auditoría de Ventas, Ingresos', person:'Jose Roberto', due:'2019.03.20', status:'ongoing', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.' },
        {title: 'Auditoría de Ventas, Ingresos Carga', person:'Carolina Delgado', due:'2019.03.25', status:'ongoing', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.'},
        {title: 'Auditoría de Planificación de Inventarios', person:'Luz Dary Puerto', due:'2019.04.01', status:'completed', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.'},
        {title: 'Auditoría de flota O6', person:'Jhon Caballero', due:'2019.02.31', status:'overdue', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.'},
        {title: 'Auditoría de Compensaciones', person:'Jose Roberto', due:'2019.03.20', status:'ongoing', content: 'Lorem ipsum dolor sit amet consectetur, adipisicing elit. Excepturi praesentium, commodi reiciendis repudiandae nisi, iste distinctio doloremque sint quis voluptatum maiores fugit provident? Harum beatae ad, est vero iste nostrum.' }
      ]
    }
  },
  computed: {
    myProjects(){
      return this.projects.filter(project => {
        return project.person === 'Jose Roberto'
      })
    }
  }

}
</script>

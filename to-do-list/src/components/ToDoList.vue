<template>
  <h1>{{ titulo }}</h1>
  <div class="formulario">
    <input v-model="tareaNueva" />
    <button v-on:click="agregarElemento">Add</button>
  </div>

  <h2>Tareas Pendientes</h2>
  <p v-if="tareasPendientes === 0">
    <span>No hay tareas pendientes</span>
  </p>
  <ul v-else>
    <li v-for="(tarea, index) in listaDeTareas" v-bind:key="index">
      {{ index }}-{{ tarea }}
      <button v-on:click="Completar(index)">Completar</button>
      <button v-on:click="Editar(tarea)">Editar</button>
    </li>
  </ul>
  <!-- <pre>
    {{ listaDeTareas }}
  </pre> -->

  <h2>Tareas Completadas</h2>
  <p v-if="ContadorDeTareasCompletadas === 0">
    <span>No hay tareas completadas</span>
  </p>
  <ul v-else>
    <li v-for="(listaEliminados, index) in tareasCompletadas" v-bind:key="index">
      {{ listaEliminados }}
    </li>
  </ul>

  <h2>
    Resumen de tareas
  </h2>
  <!-- length muestra el tamaño de la lista -->
  <p>Completadas: {{ ContadorDeTareasCompletadas }} | Pendientes: {{ tareasPendientes }}</p>
  <p>Total de tareas: {{ totalDeTareas }}</p>
  <hr>
  <editor-de-to-do-list v-if="MostrarEditor" v-bind:tarea="tareaQueEstoyEditando" v-bind:indice="index"/>
</template>

<script>
import EditorDeToDoList from './EditorDeToDoList.vue'

export default {
  data() {
    return {
      titulo: 'Aprendizaje de Vue',
      listaDeTareas: ['Instalar Vue', 'Abrirlo en el navegador'],
      tareaNueva: '',
      tareasCompletadas: [],
      MostrarEditor: false,
      tareaQueEstoyEditando:"",

    }
  },

  computed:{
    tareasPendientes(){
      return this.listaDeTareas.length

    },

    ContadorDeTareasCompletadas(){
      return this.tareasCompletadas.length
    },

    totalDeTareas(){
      return this.tareasPendientes + this.ContadorDeTareasCompletadas
    }

  },

  methods: {
    agregarElemento() {
      this.listaDeTareas.push(this.tareaNueva)
    },

    Completar(index) {
      //   alert('Eliminar elemento en la posición #' + index)
      this.tareasCompletadas.push(this.listaDeTareas[index])
      this.listaDeTareas.splice(index, 1)
    },

    Editar(tarea){
      this.MostrarEditor = true
      this.tareaQueEstoyEditando = tarea


    },

  },

  components:{
      'editor-de-to-do-list': EditorDeToDoList
    },
}
</script>



<style scoped>
h3 {
  color: black !important;
}

.formulario {
  display: block;
  background-color: red;
}
</style>

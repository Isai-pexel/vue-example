<template>
  <section>
<<<<<<< HEAD
    <h1>Editar to-do:  {{indice}} - {{ tarea }}</h1>
    <input v-bind:value="tarea"/>
    <button>Guardar</button>
=======
    <h1>Editar to-do: {{ indice }}-{{ tarea }}</h1>
    <input v-bind:value="tarea" />
    <button>Guardar</button>

    <h1>{{ textoDeEjmplo }}</h1>
>>>>>>> 6406a0f277aaf56e9c7a23a93b5dc4c8d0eb8150
  </section>
</template>

<script>
<<<<<<< HEAD

export default {
  props: {
    tarea:{
      type: String,

    },
    indice:{
      type: Number,
    }
=======
export default {
  props: {
    tarea: {
      type: String,
    },
    indice: {
      type: Number,
    },
    fecha: {
      type: String,
    },
    textoDeEjmplo: {
      type: String,
    },
>>>>>>> 6406a0f277aaf56e9c7a23a93b5dc4c8d0eb8150
  },
}
</script>
aSdasd

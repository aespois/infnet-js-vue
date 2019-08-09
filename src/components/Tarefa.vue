<template>
  <div>
    <span>{{ tarefa.id }}</span>
    {{ tarefa.title }}
    <span v-if="tarefa.completed" class="feito">Feito!</span>
    <button v-else @click="feito(tarefa)">feito</button>
  </div>
</template>

<script>
  export default {
    name: "Tarefa",
    props: {
      tarefa: Object
    },
    methods: {
      feito(t) {
        t.completed = true
      }
    }
  }
</script>

<style scoped>

</style>
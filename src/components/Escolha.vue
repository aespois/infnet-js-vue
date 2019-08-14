<template>
  <ul>
    <li v-for="item in cores" :key="item"
        @click="marcar(item)">
      {{ item }}
      <span v-if="value === item"> * </span>
    </li>
  </ul>
</template>

<script>
  export default {
    name: "Escolha",
    props: {
      cores: Array,
      value: String
    },
    methods: {
      marcar(item){
        this.$emit('input', item)
      }
    }
  }
</script>

<style scoped>

</style>
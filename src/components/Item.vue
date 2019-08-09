<template>
  <span @click="modificar">
    {{ item.nome }}
  </span>
</template>

<script>
  export default {
    name: "Item",
    props:{
      item: Object
    },
    methods: {
      modificar(){
        this.item.nome = this.item.nome + '--'
      }
    }
  }
</script>

<style scoped>

</style>
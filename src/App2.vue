<template>
  <div>
    <div v-for="item in itens" :key="item.id">
      <Item :item="item"></Item>
    </div>

    <div v-for="item in itens" :key="item.id">
      {{ item.nome }}
    </div>
  </div>
</template>

<script>
  import Item from "@/components/Item"
  export default {
    name: "App2",
    components: {Item},
    data() {
      return {
        itens: [
          { id: 1, nome: 'jorge'},
          { id: 2, nome: 'jorge asd'},
          { id: 3, nome: 'jorge malsd'},
        ]
      }
    }
  }
</script>

<style scoped>

</style>
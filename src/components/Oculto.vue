<template>
  <td>
    <span v-if="exibindo">
      {{ valor }}
    </span>
    <span v-else>***</span>
    <i @click="alternar">O</i>
  </td>
</template>
<script>
  export default {
    name: 'Oculto',
    props: {
      valor: String,
    },
    data() {
      return {
        exibindo: false
      }
    },
    computed: {
      exibido(){
        if(this.exibindo){
          return this.valor
        }
        return '***'
      }
    },
    methods: {
      alternar(){
        this.exibindo = !this.exibindo
      }
    }
  }
</script>

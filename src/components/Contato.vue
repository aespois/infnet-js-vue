<template>
  <li>
    {{ registro.nome }} -
    <a :href="registro.telefone | link_telefone">{{ registro.telefone }}</a>-
    <a :href="registro.email | link_email"> {{ registro.email }}</a>
    <button @click="alterar(registro)">alterar</button>
    <button @click="evento_excluir(registro)">excluir</button>
  </li>
</template>

<script>
  export default {
    name: "Contato",
    props: {
      registro: Object,
      alterar: Function,
    },
    filters:{
      link_telefone: function (value) {
        let n = value;
        if(value.length === 9){
          n = '5521' + value
        }
        if(value.length === 11){
          n = '55' + value
        }
        return 'https://wa.me/' + n
      },
      link_email: function (value) {
        return 'mailto:' + value
      }
    },
    methods: {
      evento_excluir(registro){
        this.$emit('deletar', registro)
      }
    }
  }
</script>

<style scoped>

</style>
<template>
  <div>
    <button @click="ordenar">ordenar</button>
    <div v-if="agenda">
      <ul>
        <Contato v-for="registro in agenda" :key="registro.id"
                 :registro="registro"
                 :alterar="alterar"
                 @deletar="receber_evento"
        ></Contato>
      </ul>
    </div>
  </div>
</template>
<script>
  import Contato from "@/components/Contato"

  export default {
    name: 'ListaContato',
    components: {Contato},
    props: {
      agenda: {},
      alterar: {},
      excluir: {},
      ordenar: {}
    },
    methods: {
      receber_evento(registro){
        this.excluir(registro)
      }
    }
  }
</script>

<template>
  <tr>
    <td>
      <input v-if="editando" v-model="item.site">
      <span v-else>{{ item.site }}</span>
    </td>
    <td>
      <input v-if="editando" v-model="item.usuario">
      <span v-else>{{ item.usuario }}</span>
    </td>
    <td v-if="editando">
      <input v-if="editando" v-model="item.senha">
    </td>
    <Oculto v-else :valor="item.senha"/>
    <td v-if="editando">
      <span @click="editar">salvar</span>
    </td>
    <td v-else>
      <span @click="editar">editar</span> |
      <span @click="remover">remover(item)</span>
    </td>
  </tr>
</template>
<script>
  import Oculto from "@/components/Oculto"

  export default {
    name: 'LinhaTabela',
    components: { Oculto },
    data() {
      return {
        editando: false
      }
    },
    props: {
      item: Object,
      remover: Function,
    },
    methods: {
      editar(){
        this.editando = !this.editando
      }
    }
  }
</script>
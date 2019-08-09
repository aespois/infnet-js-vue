<template>
  <div id="app">
    <h2>Agenda</h2>
    <div>
      <label>Nome
        <input v-model="novo_registro.nome" type="text">
      </label>
      <label>Telefone
        <input v-model="novo_registro.telefone" type="tel">
      </label>
      <label>Email
        <input v-model="novo_registro.email" type="email">
      </label>
    </div>
    <button @click="salvar" >salvar</button>
    <div v-if="agenda">
      <ul>
        <li v-for="registro in agenda" :key="registro.id">
          {{ registro.nome }} -
          {{ registro.telefone }} -
          {{ registro.email }}
          <button @click="alterar(registro)">alterar</button>
          <button @click="excluir(registro)">excluir</button>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  name: 'app',
  data() {
    return {
      novo_registro: {
        nome: '',
        telefone: '',
        email: ''
      },
      agenda: [
        {id: 1, nome: 'ezequiel', email: 'asd@asd.com', telefone: '2183838383'},
        {id: 2, nome: 'joao', email: 'joao@asd.com', telefone: '21855555583'},
        {id: 3, nome: 'maria', email: 'maria@asd.com', telefone: '21844444443'},
      ],
      count: 10
    }
  },
  methods: {
    salvar() {
      this.agenda.push({
        ...this.novo_registro,
        id: this.count
      })
      this.novo_registro = {
        nome: '',
        telefone: '',
        email: '',
      }
      this.count++
    },
    alterar(registro) {
      this.novo_registro = registro

    },
    excluir(registro) {

    },
  },
}
</script>

<style>
</style>

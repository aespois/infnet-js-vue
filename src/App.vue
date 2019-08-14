<template>
  <div id="app">
    <h2>Agenda</h2>
    <Formulario :erros="erros" :novo_registro="novo_registro" :salvar="salvar"/>
    <ListaContato :agenda="agenda" :alterar="alterar" :excluir="excluir" :ordenar="ordenar"/>
  </div>
</template>
<script>
  import ListaContato from "@/components/ListaContato"
  import Formulario from "@/components/Formulario"

  const RE_EMAIL = new RegExp(/^([A-Z|a-z|0-9](\.|_){0,1})+[A-Z|a-z|0-9]@([A-Z|a-z|0-9])+((\.){0,1}[A-Z|a-z|0-9]){2}\.[a-z]{2,3}$/gm)
  export default {
    name: 'app',
    components: {Formulario, ListaContato},
    data() {
      return {
        novo_registro: {
          nome: '',
          telefone: '',
          email: ''
        },
        erros: {
          nome: '',
          telefone: '',
          email: '',
        },
        agenda: [
          {id: 2, nome: 'joao', email: 'joao@asd.com', telefone: '987654321'},
          {id: 3, nome: 'maria', email: 'maria@asd.com', telefone: '5521987654321'},
          {id: 1, nome: 'ezequiel', email: 'asd@asd.com', telefone: '40987654321'},
        ],
        count: 10
      }
    },
    methods: {
      salvar() {
        if (!this.validar()) {
          return
        }
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
      ordenar(){
        this.agenda.sort((a, b) => a.nome.localeCompare(b.nome))
      },
      alterar(registro) {
        this.novo_registro = registro
      },
      excluir(registro) {
        let index = this.agenda.indexOf(registro)
        this.$delete(this.agenda, index)
      },
      validar() {
        this.erros = {
          nome: '',
          telefone: '',
          email: '',
        }

        if (!this.novo_registro.nome) {
          this.erros.nome = 'Preencha o nome'
        } else if (this.novo_registro.nome.split(' ').length <= 1) {
          this.erros.nome = 'Preencha o nome completo'
        }

        if (!this.novo_registro.telefone) {
          this.erros.telefone = 'Preencha o telefone'
        } else if (!this.novo_registro.telefone.lenght >= 9 || !Number(this.novo_registro.telefone)) {
          this.erros.telefone = "preencha um telefone valido"
        }

        if (!this.novo_registro.email) {
          this.erros.email = 'Preencha o email'
        } else if (!RE_EMAIL.test(this.novo_registro.email)) {
          this.erros.email = "preencha um email valido"
        }

        return !(this.erros.nome || this.erros.telefone || this.erros.email)
      }
    },
  }
</script>


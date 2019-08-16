<template>
  <div>
    <div>
      <label>
        Site: <input v-model="novo.site">
      </label>
    </div>
    <div>
      <label>
        usuario: <input v-model="novo.usuario">
      </label>
    </div>
    <div>
      <label>
        senha: <input v-model="novo.senha">
        <button @click="gerarSenha">Gerar</button>
      </label>
    </div>
    <div>
      <button @click="salvar">Novo</button>
    </div>
    <table>
      <tr>
        <th>Site</th><th>Usuario</th><th>Senha</th><th>-</th>
      </tr>
      <LinhaTabela :item="item"
                   v-for="item in lista"
                   :key="item.id"
                   :remover="remover"
      />
    </table>
  </div>
</template>

<script>
  import LinhaTabela from "@/components/LinhaTabela"

  export default {

    name: "AppSenhas",
    components: {LinhaTabela},
    data() {
      return {
        novo: { site: '',  usuario: '', senha:'' },
        lista: [],
        count: 0
      }
    },
    methods:{
      salvar() {
        if(!this.validar()) {
          return
        }
        this.lista.push(this.novo)
        this.novo = { id: this.count++, site: '',  usuario: '', senha:'' }
      },
      validar(){
        return this.novo.site && this.novo.usuario && this.novo.senha
      },
      remover(item){
        let posicao = this.lista.indexOf(item)
        this.$delete(this.lista, posicao)
      },
      gerarSenha() {
        const MAPA = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%&'
        let senha = ''
        for(let i = 0; i < 8; i++){
          senha += MAPA[
            Math.floor(
              Math.random() * MAPA.length
            )]
        }
        this.novo.senha = senha
      }

    }

  }
</script>


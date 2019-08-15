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
        <th>Site</th><th>Usuario</th><th>Senha</th><th></th>
      </tr>
      <tr v-for="item in lista" :key="item.site">
        <td>{{ item.site }}</td>
        <td>{{ item.usuario }}</td>
        <Oculto :valor="item.senha"/>
      </tr>
    </table>
  </div>
</template>

<script>
  import Oculto from "@/components/Oculto"

  export default {

    name: "AppSenhas",
    components: {Oculto},
    data() {
      return {
        novo: { site: '',  usuario: '', senha:'' },
        lista: []
      }
    },
    filters: {
      ocultar(valor){
        return '***'
      }
    },
    methods:{
      salvar() {
        this.lista.push(this.novo)
        this.novo = { site: '',  usuario: '', senha:'' }
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


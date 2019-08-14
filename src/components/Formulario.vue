<template>
  <div>
    <div>
      <Campo nome="Nome" tipo="text"
             :erro="erros.nome"
             v-model="novo_registro.nome"/>

      <Campo nome="Telefone" tipo="tel"
             :erro="erros.telefone"
             v-model="novo_registro.telefone"/>

      <Campo nome="Email" tipo="email"
             :erro="erros.email"
             v-model="novo_registro.email"/>
    </div>
    <button @click="salvar">novo</button>
  </div>
</template>
<script>
  import Campo from "@/components/Campo"

  export default {
    name: 'Formulario',
    components: {Campo},
    props: {
      erros: {},
      novo_registro: {},
      salvar: {}
    }
  }
</script>
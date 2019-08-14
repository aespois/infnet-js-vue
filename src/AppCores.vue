<template>
  <div>
    Cores
    <Escolha
        :cores="cores"
        v-model="selecionada">
    </Escolha>
    <div class="espaco"
         :style="{'background-color': selecionada}"
    ></div>
  </div>
</template>

<script>
  import Escolha from "@/components/Escolha"
  export default {
    name: "AppCores",
    components: {Escolha},
    data() {
      return {
        cores: ['blue', 'green', 'red'],
        selecionada: ''
      }
    }
  }
</script>
<style scoped>
  .espaco{
    width: 100px;
    height: 100px;
    display: block;
  }
</style>
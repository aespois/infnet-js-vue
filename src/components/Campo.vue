<template>
  <div>
    <label>{{ nome }}
      <input :value="value" :type="tipo" @input="altera($event)">
      <span v-if="erro">{{ erro }}</span>
    </label>
  </div>
</template>
<script>
  export default {
    name: 'Campo',
    props: {
      value: String,
      erro: String,
      nome: String,
      tipo: String
    },
    methods: {
      altera($event){
        this.$emit('input', $event.target.value)
      }
    }
  }
</script>
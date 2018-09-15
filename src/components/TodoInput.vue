<template>
    <input type="text" :value="value" v-on="inputListeners">
</template>

<script>
export default {
  name: "TodoInput",
  props: {
    value: {
      type: String,
      default: ""
    }
  },
  computed: {
    inputListeners: function () {
      var vm = this
      // `Object.assign` combina objetos para formar un nuevo objeto
      return Object.assign({},
        // Agregamos todos los listeners del padre
        this.$listeners,
        // Agregamos listener personalizados
        {
          // Esto asegura que el componente funciona con v-model
          input: function (event) {
            vm.$emit('input', event.target.value)
          }
        }
      )
    }
  },
};
</script>


<style scoped>
input {
  width: 100%;
  padding: 10px 10px;
  border: 1px solid #42b983;
}
</style>


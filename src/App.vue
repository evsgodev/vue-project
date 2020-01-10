<template>
  <div id="app">
    <InputText/>
  </div>
</template>

<script>
import InputText from './components/ui/InputText.vue'

export default {
  name: 'app',
  components: {
    InputText,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 30px;
}

.ql-editor {
    max-height: 194px;
}

.form-group {
    margin-bottom: 20px;
}

.row {
    margin: 0 -15px;
}

[class*="col-"] {
    padding-left: 15px;
    padding-right: 15px;
}

</style>

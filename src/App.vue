<template>
<h1>Memo App</h1>
<ItemList />
</template>

<script>
import ItemList from './components/ItemList.vue'

export default {
  name: 'App',
  components: { ItemList },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 20px;
  background: white;
  width: 100%;
  height: 600px;
}
body {
  background: gainsboro;
}
</style>

<template>
<h1>Memo App</h1>
<ItemList @editArea="openEditArea" />
<span v-if="showEdit">
  <EditItem />
</span>
</template>

<script>
import ItemList from './components/ItemList.vue'
import EditItem from './components/EditItem.vue'

export default {
  name: 'App',
  components: { ItemList, EditItem },
  data() {
    return {
      showEdit: false
    }
  },
  methods: {
    openEditArea() {
     this.showEdit = true
    }
  }
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

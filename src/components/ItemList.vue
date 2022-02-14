<template>
  <ul>
    <li v-for="item in items" :key="item.id">
      <p @click="edit">{{ firstLine(item.body) }}</p>
    </li>
    <li @click="newMemo">＋</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      items: [{id: 1, body: `memo1\nmemo1\nmemo1`},
              {id: 2, body: `memo2\nmemo2\nmemo2`},
              {id: 3, body: `memo3\nmemo3\nmemo3`}]
    }
  },
  methods: {
    edit() {
      console.log('edit clicked!')
    },
    newMemo() {
      this.items.push({id:4, body: `新規メモ`})
      this.$emit('editArea')
    }
  },
  computed: {
    firstLine: function() {
      return function(body) {
        return String(body.split('\n', 1))
      }
    }
  }
}
</script>

<style>
ul {
  width: 300px;
  padding-inline-start: 20px;
  display: inline-block;
  vertical-align: top;
  margin: 0;
}

li {
  list-style-type: none;
  text-decoration: underline;
  padding: 5px 0;
}

li:hover {
  color: blue;
  cursor: pointer;
}

p {
  margin: 0;
}
</style>

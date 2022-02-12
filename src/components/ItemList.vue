<template>
  <ul>
    <li v-for="item in items" :key="item.id">
      <p @click="edit">{{ firstLine(item.body) }}</p>
    </li>
    <li @click="edit">＋</li>
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
li {
  list-style-type: none;
  text-decoration: underline;
}
li:hover {
  color: blue;
  cursor: pointer;
}
</style>

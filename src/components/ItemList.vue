<template>
  <ul>
    <li v-for="(item, index) in items" :key="item.id">
      <p @click="editMemo(index)">{{ firstLine(item.body) }}</p>
    </li>
    <li @click="newMemo">＋</li>
  </ul>
  <form @submit.prevent="setMemo" v-if="showEditForm">
    <textarea name="body" cols="40" rows="15" v-model="body"></textarea>
    <input type="submit" value="編集">
    <input type="button" value="削除" @click="deleteMemo(editIndex)">
  </form>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      body: '',
      editIndex: '',
    }
  },
  mounted() {
    this.items = JSON.parse(localStorage.getItem('items')) || []
  },
  methods: {
    editMemo(index) {
      this.body = this.items[index].body
      this.editIndex = index
    },
    newMemo() {
      this.items.push({id: Date.now(), body: `新規メモ`})
      this.editIndex = this.items.length - 1
      this.body = this.items[this.editIndex].body
    },
    setMemo() {
      if (this.body) {
        this.items[this.editIndex].body = this.body
        localStorage.setItem('items', JSON.stringify(this.items))
      }
      this.body = ''
      this.editIndex = ''
    },
    deleteMemo(editIndex) {
      if (confirm('削除しますか？')) {
        this.items.splice(editIndex, 1)
        localStorage.setItem('items', JSON.stringify(this.items))
        this.body = ''
        this.editIndex = ''
      }
    }
  },
  computed: {
    firstLine: function() {
      return function(body) {
        return String(body.split('\n', 1))
      }
    },
    showEditForm() {
      return this.editIndex !== ''
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

form {
  display: inline-block;
}

textarea {
  margin: 10px 20px;
  display: block;
}

input {
  margin: 10px 0 0 20px;
  width: 75px;
}
</style>

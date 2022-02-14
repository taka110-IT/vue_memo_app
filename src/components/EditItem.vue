<template>
<form>
  <textarea name="body" cols="40" rows="15"></textarea>
  <input type="submit" value="編集">
  <input type="submit" value="削除">
</form>
</template>

<script>
export default {

}
</script>

<style>
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

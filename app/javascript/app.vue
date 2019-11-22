<template>
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>まずはデータを表示</title>
</head>
<body>

<div id="app">
  <p>
  <input type="text"
    placeholder="TODOを入力しましょう！"
    v-model="newItemTitle"
    v-on:keyup.enter="addTodo(newItemTitle)">
  </p>

  <ul>
    <li v-for="item in items">
      <label v-bind:class="{ done: item.isChecked }">
        <input type="checkbox" v-model="item.isChecked"> {{ item.title }}
      </label>
    </li>
  </ul>
</div>

</body>
</html>
</template>

<script>
export default {
  el: '#app',
  data: function () {
    return {
      items: [
          { title: 'test1', isChecked: true },
          { title: 'test2', isChecked: true },
          { title: 'test3', isChecked: false },
          { title: 'test4', isChecked: false },
          { title: 'test5', isChecked: false },
          { title: 'test6', isChecked: false },
      ],
      newItemTitle: ''
    }
  },

  methods: {
    addTodo: function(newTitle){
      this.items.push({
        title: newTitle,
        isChecked: false
      });
      this.newItemTitle = ''; //追加
    },
  },
}
</script>

<style scoped>
p {
  font-size: 2em;
  text-align: center;
}

.done { text-decoration: line-through; }
</style>

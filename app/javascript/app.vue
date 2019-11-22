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
    v-on:keyup.enter="addTodo">
  </p>

  <ul>
    <li v-for="item in items">
      <label>
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
          { title: '領収書を準備する', isChecked: true },
          { title: 'Vue.jsハンズオンの資料を作る', isChecked: true },
          { title: '参加者の人数を確認する', isChecked: false },
          { title: 'ピザを注文する', isChecked: false },
          { title: '参加費のお釣りを準備する', isChecked: false },
          { title: '会場設営をする', isChecked: false },
      ],
      newItemTitle: ''
    }
  },

  methods: {
    addTodo: function(){
      this.items.push({
        title: this.newItemTitle,
        isChecked: false
      });
    },
  },
}
</script>

<style scoped>
p {
  font-size: 2em;
  text-align: center;
}
</style>

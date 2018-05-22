<!--app.vue是我们的主组件，所有页面都是在App.vue下进行切换的,app.vue在所有页面都有，通常将公用的组件放在里面-->
<template>
  <div id="app"><!--ID 选择器-->
    <h1 v-text= "title"> </h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
    <li v-for="item in items" :key="item.id" v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinish(item)">
        {{item.label}}
    </li>
    </ul>
    <p>child tells me: {{ childWords }}</p>
    <component-a msgfromfather='you win!' v-on:child-tell-me-somthing='listenToMyBoy'></component-a>
  </div>
</template>

<script>
import Store from './store'
import ComponentA from './components/componentA'
console.log(Store)
export default {
  data: function () {
    return {
      title: 'this is a todo list',
      items: Store.fetch(),
      newItem: '',
      childWords: ''
    }
  },
  components: { ComponentA },
  watch: {
    items: {
      handler: function (items) {
        Store.save(items)
      },
      deep: true
    }
  },
  methods: {
    toggleFinish: function (item) {
      item.isFinished = !item.isFinished
    },
    addNew: function () {
      this.items.push({
        label: this.newItem,
        isFinished: false
      })
      this.newItem = ''
    },
    listenToMyBoy: function (msg) {
      this.childWords = msg
    }
  }
}
</script>

<style>
.finished{
  text-decoration: underline;
}
html {
  height: 100%;
}
body{
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;/*font-family 规定元素的字体系列*/
  -webkit-font-smoothing: antialiased;/*针对图标字体进行抗锯齿渲染。*/
  -moz-osx-font-smoothing: grayscale;/*Firefox implements a similar property, but with different values: -moz-osx-font-smoothing. It only works on Mac OS X/macOS.*/
  text-align: center;
  color: #0879eb;
  margin-top: 20px;
}
</style>

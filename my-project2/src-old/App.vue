<!--app.vue是我们的主组件，所有页面都是在App.vue下进行切换的,app.vue在所有页面都有，通常将公用的组件放在里面-->
<template>
  <div id="app"><!--ID 选择器-->
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;/*font-family 规定元素的字体系列*/
  -webkit-font-smoothing: antialiased;/*针对图标字体进行抗锯齿渲染。*/
  -moz-osx-font-smoothing: grayscale;/*Firefox implements a similar property, but with different values: -moz-osx-font-smoothing. It only works on Mac OS X/macOS.*/
  text-align: center;
  color: #0879eb;
  margin-top: 20px;
}
</style>

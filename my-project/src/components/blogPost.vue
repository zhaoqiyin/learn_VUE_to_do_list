<template>
<!--父组件通过props向子组件传递数据 -->
    <div>
        <h3>{{title}}</h3>
        <!--自组件通过事件向父组件发送消息 -->
        <button v-on:click="$emit('enlarge-text', 0.1)">Enlarge text</button>
    </div>
</template>

<script>
export default {
  props: ['title']
}
</script>

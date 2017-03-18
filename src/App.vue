<template>
  <div id="app">
    <v-header></v-header>
    <!-- 使用 router-link 组件来导航. -->
    <!-- 通过传入 `to` 属性指定链接. -->
    <!-- <router-link> 默认会被渲染成一个 `<a>` 标签 -->
    <v-tab></v-tab>
    <!-- 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>
  </div>
</template>

<script>
  import header from './components/Header.vue'
  import tab from './components/Tab.vue'

  export default {
    name: 'app',
    components: {
      'v-header': header,
      'v-tab': tab
    }
  }
</script>

<style lang="less">
  @import '~vux/src/styles/reset.less';
</style>

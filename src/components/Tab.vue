<template>
    <div>
        <tab :line-width=2 active-color='rgb(240,20,20)' v-model="TabIndex">
            <tab-item class="tab-item" :selected="TabItem === item.name" v-for="(item, index) in TabList"
                      @click="TabItem = item.name"
                      :key="index">
                <router-link :to="item.path">{{item.name}}</router-link>
            </tab-item>
        </tab>
        <swiper v-model="TabIndex" class="container" :show-dots="false">
            <swiper-item v-for="(item, index) in TabList" :key="index">
                <!-- 路由匹配到的组件将渲染在这里 -->
                <router-view></router-view>
            </swiper-item>
        </swiper>
        <router-link to="/ratings">Go to item</router-link>
    </div>

</template>

<script type="text/ecmascript-6">
  import {Tab, TabItem, Swiper, SwiperItem} from 'vux'
  export default {
    data () {
      return {
        TabList: [
          {name: '商品', path: 'goods'},
          {name: '评价', path: 'ratings'},
          {name: '商家', path: 'seller'}
        ],
        TabItem: '商品',
        TabIndex: 0
      }
    },
    components: {
      Tab,
      TabItem,
      Swiper,
      SwiperItem
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus" rel="stylesheet/stylus">
    .tab-item
        height 40px
        line-height 40px
        text-align center
        a
            font-size 14px
            display block
            width 100%
            height 100%
            color rgb(77, 85, 93)
        &.vux-tab-selected
            a
                color rgb(240, 20, 20)
</style>

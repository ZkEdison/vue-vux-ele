<template>
  <div>
    <flexbox class="tab">
      <flexbox-item class="tab-item"><router-link to="/goods">商品</router-link></flexbox-item>
      <flexbox-item class="tab-item"><router-link to="/ratings">评论</router-link></flexbox-item>
      <flexbox-item class="tab-item"><router-link to="/seller">商家</router-link></flexbox-item>
    </flexbox>
  </div>
</template>

<script type="text/ecmascript-6">
  import { Flexbox, FlexboxItem } from 'vux'
  export default {
    data () {
      return {
      }
    },
    components: {
      Flexbox,
      FlexboxItem
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus" rel="stylesheet/stylus">
  .tab
    width 100%
    height 80px
    line-height 80px
    .tab-item
      text-align center
      a
        display block
        width 100%
        height 100%
        font-size 28px
        color rgb(240,20,20)
</style>

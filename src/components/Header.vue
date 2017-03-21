<template>
    <div class="header">
        <div class="header-image" :style="{backgroundImage: 'url(' + sellerImageUrl + ')'}"></div>
        <div class="header-blur"></div>
        <div slot="content" class="header-container">
            <div class="header-top">
                <div class="left-avater">
                    <img :src="sellerImageUrl" alt="">
                </div>
                <div class="right-content">
                    <h3 class="seller-title">{{seller.name}}</h3>
                    <p>{{seller.description}}/{{seller.deliveryTime}}minute arrive</p>
                    <p v-if="seller.supports" class="supports" :class="classMap[seller.supports[0].type]">
                        {{seller.supports[0].description}}<span>{{seller.supports.length}} 个 <span class="icon-keyboard_arrow_right"></span></span></p>
                </div>
            </div>
            <div class="bottom-bulletin">
                <p class="bottom-bulletin-content">{{seller.bulletin}}</p>
            </div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
  export default {
    components: {},
    data () {
      return {
        seller: {},
        sellerImageUrl: '',
        classMap: []
      }
    },
    created () {
      this.$http.get('/api/seller')
          .then((res) => {
            console.log(res)
            if (res.data.errno === 0) {
              this.seller = res.data.data
              this.sellerImageUrl = this.seller.avatar
            }
          })
          .catch((error) => {
            console.log(error)
          })
      this.classMap = ['decrease', 'discount', 'guarantee', 'invoice', 'special']
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus" rel="stylesheet/stylus">
    @import "./../common/stylus/mixin.styl"
    /*@import "./../common/stylus/icon.styl"*/

    .header
        color #fff
        position relative
        .header-image
            position absolute
            top 0
            left 0
            bottom 0
            right 0
            z-index -2
            background-repeat no-repeat
            background-position center
            background-size cover
            filter blur(10px)
            &:after
                content ''
                position absolute
                top 0
                left 0
                bottom 0
                right 0
                z-index -1
                background-color rgba(7, 17, 27, 0.5)

    .header-container
        .header-top
            padding 24px 0 18px 24px
            position relative
            .left-avater
                display inline-block
                position absolute
                left 24px
                top 24px
                vertical-align top
                width 64px
                height 64px
                border-radius 4px
                overflow hidden
                text-align center
                img
                    width auto
                    height 100%
            .right-content
                padding 2px 0
                margin-left 80px
                .seller-title
                    padding-left 36px
                    font-size 16px
                    color rgb(255, 255, 255)
                    font-weight bold
                    line-height 18px
                    white-space nowrap
                    bg-image('./../assets/img/brand')
                    background-repeat no-repeat
                    background-position left center
                    background-size 30px auto
                p
                    font-size 12px
                    font-weight 200
                    line-height 12px
                    margin-top 9px
                .supports
                    position relative
                    padding-left 16px
                    bg-image('./../assets/img/decrease_1')
                    background-size auto 100%
                    background-position left center
                    background-repeat no-repeat
                    &.decrease
                        bg-image('./../assets/img/decrease_1')
                    &.discount
                        bg-image('./../assets/img/discount_1')
                    &.guarantee
                        bg-image('./../assets/img/guarantee_1')
                    &.invoice
                        bg-image('./../assets/img/invoice_1')
                    &.special
                        bg-image('./../assets/img/special_1')
                    span
                        position absolute
                        top 50%
                        right 12px
                        padding 7px 8px
                        border-radius 7px
                        background-color rgba(0, 0, 0, 0.2)
                        transform translateY(-50%)
        .bottom-bulletin
            height 28px
            line-height 28px
            font-size 10px
            color: #fff
            padding 0 16px
            background-color rgba(7, 17, 27, 0.2)
        .bottom-bulletin-content
            white-space nowrap
            text-overflow ellipsis
            overflow hidden
            padding-right 4px
            padding-left 26px
            bg-image('./../assets/img/bulletin')
            background-repeat no-repeat
            background-size 22px auto
            background-position left center

</style>

<template>
  <div class="header">
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
    data () {
      return {
        seller: {}
      }
    },
    created () {
      this.$http.get('/api/seller')
        .then((res) => {
          console.log(res)
          if (res.data.errno === 0) {
            this.seller = res.data.data
          }
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus" rel="stylesheet/stylus">

</style>

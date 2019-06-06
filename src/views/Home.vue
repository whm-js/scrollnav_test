<template>
  <div style="height:100%;">
        <cube-scroll-nav @change="changeHandler">
          <template slot="prepend">
          <div style="height:100px;" v-for="(item,index) in 3" :key="index">prepend内容</div>
          </template>
          <cube-scroll-nav-panel
            v-for="item in data"
            :key="item.name"
            :label="item.name">
            <ul>
              <li v-for="(food,index) in item.foods" :key="index">
                <div>
                  <img :src="food.icon">
                  <p>{{food.name}}</p>
                </div>
              </li>
            </ul>
          </cube-scroll-nav-panel>
        </cube-scroll-nav>
  </div>
</template>

<script type="text/ecmascript-6">
  // import CubePage from '../../components/cube-page.vue'
  import goodsData from '@/components/goods-list.json'
  const goods = goodsData.goods
  export default {
    components: {
      // CubePage
    },
    data() {
      return {
        data: goods
      }
    },
    methods: {
      changeHandler(label) {
        console.log('changed to:', label)
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
    .view-wrapper
      position: fixed
      top: 0
      left: 0
      bottom: 0
      width: 100%
    .cube-scroll-nav-bar
      border-bottom: 1px solid #f4f4f4
    .cube-scroll-nav-panel
      width: 90%
      margin: auto
      img
        width: 114px
        height: 114px
      ul
        overflow: hidden
        font-size: 14px
        line-height: 1.4
        color: #666
      li
        float: left
        width: 50%
        div
          width: 114px
          margin: 0 auto 15px
          p
            overflow: hidden
            white-space: nowrap
            text-overflow: ellipsis
    .cube-scroll-nav-panel-title
      padding: 15px
      font-size: 16px
      text-align: center
</style>
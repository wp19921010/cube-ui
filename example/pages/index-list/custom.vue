<template>
  <cube-page type="index-list" title="IndexList">
    <div slot="content">
      <div class="view-wrapper">
        <div class="index-list-wrapper">
          <cube-index-list
            :data="cityData"
            :title="title"
            @title-click="clickTitle">
            <cube-index-list-group v-for="(group, index) in cityData" :key="index" :group="group">
              <cube-index-list-item v-for="(item, index) in group.items" :key="index" :item="item" @select="selectItem">
                我是自定义{{item.name}}
              </cube-index-list-item>
            </cube-index-list-group>
          </cube-index-list>
        </div>
      </div>
    </div>
  </cube-page>
</template>

<script type="text/ecmascript-6">
  import CubePage from '../../components/cube-page.vue'
  import cityData from '../../data/index-list.json'

  export default {
    components: {
      CubePage
    },
    data() {
      return {
        title: 'Current City: BEIJING',
        cityData: cityData
      }
    },
    methods: {
      selectItem(item) {
        console.log(item.name)
      },
      clickTitle(title) {
        console.log(title)
      }
    }
  }

</script>

<style lang="stylus" rel="stylesheet/stylus">
  .view-wrapper
    position: fixed
    top: 54px
    left: 0
    bottom: 0
    width: 100%
    .index-list-wrapper
      height: 98%
      width: 94%
      margin: 0 auto
      overflow: hidden
</style>

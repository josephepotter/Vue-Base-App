<template>
  <div id="app">
    <navbar :navData="navData" />
    <banner />
    <router-view/>
  </div>
</template>

<script>
import navbar from '@/components/navbar'
import banner from '@/components/banner'
export default {
  data () {
    return {
      navData:{
        mainLink:{
          text:'Home',
          url:'/'
        },
        primaryLinkList: [
          {
            text:'link1',
            url:'/'
          },
          {
            text:'link2',
            url:'/'
          },
          {
            text:'link3',
            url:'/'
          }
        ],
        secondaryLinkList: [
          {
            text:'account',
            url:'/',
            icon: 'face'
          },
          {
            text:'link5',
            url:'/'
          }
        ]
      }
    }
  },
  components: {
      'navbar': navbar,
      'banner': banner
  },
  name: 'App'
}
</script>

<style lang="less">
  @import "./assets/css/colors.less";
  @import "./assets/css/variables.less";
  body{
    margin: 0px;
    color: @primary-text-color;
    font-family: @primary-font;
  }
</style>

<template>
  <div id="navbar">
    <div id="primary-link-holder" class="link-holder">
      <span id="main-link" class="link">
        <i v-if="navData.mainLink.icon" class="material-icons icon">{{navData.mainLink.icon}}</i>
        {{navData.mainLink.text}}
      </span>
      <span id="menu-button" class="link" v-if="showMenuButton" v-on:click="setNavHeight"><i class="material-icons icon">menu</i></span>
      <!--TODO: make the following list of links a component-->
      <a v-for="link in navData.primaryLinkList" :href="link.url" class="link">
        <i v-if="link.icon" class="material-icons icon">{{link.icon}}</i></span>
        {{link.text}}
      </a>
    </div>
    <div id="secondary-link-holder" class="link-holder">
      <a v-for="link in navData.secondaryLinkList" :href="link.url" class="link">
        <i v-if="link.icon" class="material-icons icon">{{link.icon}}</i></span>
        {{link.text}}
      </a>
    </div>
  </div>
</template>

<script>
import '../assets/css/navbar.less'
export default {
  name: 'navbar',
  props: ['navData'],
  data () {
    return {
      showMenuButton: false
    }
  },
  methods:{
    pageResize(){
      if (window.innerWidth > 768) {
        this.$el.style.height = this.$el.getElementsByClassName('link')[0].clientHeight + 'px'
        this.showMenuButton = false;
      }
      else {
        this.showMenuButton = true;
      }
    },
    setNavHeight(){
      console.log("things");
      const links = this.$el.getElementsByClassName('link');
      const linkCount = links.length - 1;
      const height = links[0].clientHeight;
      console.log(height);
      console.log(this.$el.style.height);
      if (this.$el.style.height !== height + "px" && this.$el.style.height !== '') {
        this.$el.style.height = height + "px";
      }
      else {
        const fullHeight = linkCount*height;
        console.log(fullHeight);
        this.$el.style.height = fullHeight + "px";
      }
    }
  },
  mounted(){
    this.pageResize();
    window.onresize = this.pageResize;
  }
}
</script>

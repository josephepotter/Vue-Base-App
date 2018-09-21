<template>
  <div>
    <div class="banner">
      <div class="banner-side" v-on:click="moveLeft">
      </div>
      <div class="banner-middle">
        <p class="all-title">Welcome to your online recipe store!</p>
        <div class="banner-track">
          <span class="item">
            <img class="item-image shadow" src="https://wallpaperbrowse.com/media/images/3848765-wallpaper-images-download.jpg"/>
          </span>
          <span class="item">
            <img class="item-image shadow" src="https://wallpaperbrowse.com/media/images/beautiful-sunset-images-196063.jpg"/>
          </span>
          <span class="item">
            <img class="item-image shadow" src="https://www.planwallpaper.com/static/images/6775415-beautiful-images.jpg"/>
          </span>
        </div>
      </div>
      <div class="banner-side" v-on:click="moveRight">
      </div>
    </div>
  </div>
</template>

<script>
  import '../assets/css/banner.less'
  export default {
    name: 'banner',
    props: ['navData'],
    data () {
      return {
       count: 3,
       position: 0
     };
    },
    methods:{
      moveLeft(){
        let track = document.querySelector(".banner-track");
        let position = this.position;
        position--;
        if(position < 0){
          position = 0
        }
        let newLeft = position * (-100);
        this.position = position;
        //https://stackoverflow.com/questions/1806246/jquery-move-element-by-relative-value?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa
        track.style.left = newLeft + '%';
      },
      moveRight(){
        let track = document.querySelector(".banner-track");
        let position = this.position;
        position++;
        if(position > (this.count -1)){
          position = this.count -1;
        }
        let newLeft = position * (-100);
        this.position = position;
        //https://stackoverflow.com/questions/1806246/jquery-move-element-by-relative-value?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa
        track.style.left = newLeft + '%';
        }
    },
    mounted(){
      let track = document.querySelector(".banner-track");
      track.style.width = (this.count * 100) + "%";
    }

  }
</script>

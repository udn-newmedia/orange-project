<template>
  <div v-if="showAD">
    <div class="bannerModel" :style="{backgroundColor: backgroundColor}" :class="{skewIn: canShow}" ref="banner">
      <a :href="href" target="_blank" @click="handle_GA"><img :src="srcRWD(src, srcWeb)" :alt="manufacture" :title="manufacture"></a>
    </div>
  </div>
</template>

<script>
import Utils from 'udn-newmedia-utils'
export default {

  name: 'banner',
  props: ['manufacture', 'href', 'src', 'srcWeb', 'backgroundColor', 'expire'],
  data () {
    return {
      canShow: false,
      currentDate: new Date().getTime(),
      showAD: true,
    }
  },
  computed: {
    expireDate () {
      return new Date(this.expire).getTime()
    }
  },
  methods: {
  	handle_GA: function () {
      const self = this
      ga("send", {
          "hitType": "event",
          "eventCategory": "超連結",
          "eventAction": "click",
          "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [BannerLink: " + self.href + "] [廠商名稱: " + self.manufacture + "]"
        });
  	},
    isPC: function() {
      if(window.innerWidth >= 1024) {
        return true
      } else {
        return false
      }
    },
    srcRWD: function(mob, pc){
      if(window.innerWidth <= 768){
        if(window.matchMedia("(orientation: landscape)").matches){
          return pc
        }
        else{
          return mob
        }
      }
      else{
        return pc
      }
    },
    handle_scroll () {
      let currentOffset = window.pageYOffset
      const targetOffset = this.$refs.banner.offsetTop
      const showBanner = window.pageYOffset > this.$refs.banner.offsetTop - window.innerHeight/2
      if (showBanner) {
        this.canShow = true
      }
    }
  },
  created () {
    if(this.currentDate > this.expireDate){
      this.showAD = false
    }
  },
  mounted () {
    console.log('mount')
    if(this.currentDate > this.expireDate){
      this.$destroy()
    } else {
      window.addEventListener('scroll', this.handle_scroll);
    }
  }
}
</script>

<style lang="scss" scoped>
.bannerModel{
	width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
	position: relative;
	top: 0;
	left: 0;
  padding: 20px;
  visibility: hidden;
	img{
		width: 100%;
		max-height: 100%;
	}
}
@media screen and (min-width: 1024px) {
	.bannerModel{
    padding: 50px;
	}
}
.skewIn{
  animation: skewIn 444ms linear;
  // animation: skewIn 888ms cubic-bezier(1,-0.11, 1, 1);
  animation-fill-mode: both;
}
@keyframes skewIn {
  from{
    visibility: visible;
    opacity: 0;
    transform: translate(0, 10vh)
  }
  to{
    visibility: visible;
    opacity: 1;
    transform: translate(0, 0)
  }
}
</style>

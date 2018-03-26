<template>
	<div class="bannerModel" id="bannerSet" :style="{backgroundColor: backgroundColor}">
    
  </div>
</template>

<script>
import Utils from 'udn-newmedia-utils'
export default {

  name: 'banner',
  props: ['manufacture', 'href', 'src', 'alt', 'title', 'backgroundColor'],
  data () {
    return {
      url: 'https://www.googletagservices.com/dcm/dcmads.js',
      scriptTag: '<script src=\'https://www.googletagservices.com/dcm/dcmads.js\'><\/script>'
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
        console.log("[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [BannerLink: " + self.href + "] [廠商名稱: " + self.manufacture + "]")
  	},
    isPC: function() {
      if(window.innerWidth >= 1024) {
        return true
      } else {
        return false
      }
    },
  },
  mounted () {

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
	padding: 0;
	img{
		width: 100%;
		max-height: 100%;
	}
  iframe{
    cursor: pointer;
  }
}
.iframeContainer{
  width: 100%;
  height: 250px;
  background-color: #000;
}
@media screen and (min-width: 1024px) {
	.bannerModel{
		padding: 0 10%;
	}
}
</style>
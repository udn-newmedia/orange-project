<template>
	<div :id="menuText" class="ReadMoreWrapper" :class="titlePosition" :style="{backgroundColor: backgroundColor, color: fontColor, backgroundImage: 'url('+ bgRWD() +')'}">
		<div class="title" :style="{backgroundColor: titleColor}">
			<h2>{{title}}</h2>
			<h2>{{subtitle}}</h2>
			<div class="leftBorder" :style="{borderColor: titleColor}"></div>
			<div class="rightBorder" :style="{borderColor: titleColor}"></div>
			<span v-if="useReadMore" class="toRead">{{text}}</span>
			<a class="linkBlock" :href='href' target="_blank" @click='sendGA()'></a>
		</div>
		<div class="forVideo">
			<EmbededVideo v-if="isVideo" :src="src" :srcWeb="srcWeb" :poster="poster" :posterWeb="posterWeb" customControl="yes" controlColor="#ff9a57"></EmbededVideo>
		</div>
	</div>
</template>

<script>
import Bus from '../eventBus.js'
import Utils from 'udn-newmedia-utils'
import EmbededVideo from './EmbededVideo.vue'
export default {

  name: 'ReadMore',
  components:{
  	EmbededVideo
  },
  props: ['menuText', 'position', 'title', 'subtitle', 'href', 'backgroundColor', 'titleColor', 'fontColor', 'useReadMore', 'bg', 'bgweb', 'src', 'srcWeb', 'poster', 'posterWeb'],
  data () {
    return {
    	text: '繼續閱讀'
    }
  },
  computed: {
  	titlePosition: function() {
  		if(this.position === 'left') {
  			return 'titleLeft'
  		} else if(this.position === 'right') {
  			return 'titleRight'
  		}
  	},
  	isVideo: function() {
  		if(this.src !== undefined && this.srcWeb){
  			this.text = '觀看完整影片'
  			return true
  		} else {
  			return false
  		}
  	}
  },
  methods: {
    bgRWD: function(){
      if(window.innerWidth <= 768){
          if(window.matchMedia("(orientation: landscape)").matches){
              return this.bgweb
          }
          else{
              return this.bg
          }
      }
      else{
          return this.bgweb
      }
    },
    sendGA: function() {
    	const self = this
        ga("send", {
            "hitType": "event",
            "eventCategory": "超連結",
            "eventAction": "click",
            "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + self.href + "] ["+ self.title +"]"
        });
    },
  	handle_resize: function() {
  		this.$forceUpdate()
  	},
    handle_Emit: function() {
      const self = this
      Bus.$emit('emitHeadbarTitle', {
        title: self.menuText
      })
    },  	
  },
  created() {
  	window.addEventListener('resize', this.handle_resize)
  },
  beforeDestroy () {
  	window.removeEventListener('resize', this.handle_resize)
  },
  mounted: function(){
     this.handle_Emit()
  } 	
}
</script>

<style lang="scss" scoped>
.linkBlock{
	position: absolute;
	z-inde: 50;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}
.forVideo{
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}
.ReadMoreWrapper{
	width: 100%;
	height: 100vh;
	position: relative;
	z-index: 0;
	display: flex;
	align-items: flex-end;
	padding-bottom: 50px;
	color: #fff;
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;	
}
.title{
	width: 90%;
	position: relative;
	z-index: 80;
	color: inherit;
	padding-left: 15px;
	padding-right: 15px;
	padding-bottom: 20px;
	h2{
		font-size: 26px;
		line-height: 32px;
		color: inherit;
	}
	.toRead{
		position: absolute;
		right: 5px;
		bottom: 5px;
		text-decoration: none;
		border-bottom: 1px solid #fff;
		color: inherit;
		font-size: 16px;
	}
}
.leftBorder{
	position: absolute;
	width: 33%;
	height: 30%;
	left: -10px;
	top: -10px;
	border-top: 1px solid red;
	border-left: 1px solid red;
}
.rightBorder{
	position: absolute;
	width: 33%;
	height: 30%;
	right: -10px;
	bottom: -10px;
	border-bottom: 1px solid red;
	border-right: 1px solid red;	
}
.titleLeft{
	justify-content: center !important;
}
.titleRight{
	justify-content: center !important;
}
@media screen and (min-width: 1024px) {
	.ReadMoreWrapper{
		padding: 80px;
	}
	.title{
		padding: 0 35px;
		width: 45%;
		max-width: 550px;
		padding-bottom: 50px;
		h2{
			font-size: 30px;
		}
		.toRead{
			right: 10px;
			bottom: 10px;
			font-size: 21px;
		}
	}
	.leftBorder{
		border-top: 1.5px solid red;
		border-left: 1.5px solid red;		
		width: 28%;
		height: 40%;
	}
	.rightBorder{
		border-bottom: 1.5px solid red;
		border-right: 1.5px solid red;		
		width: 28%;
		height: 40%;
	}	
	.titleLeft{
		justify-content: flex-start !important;
	}
	.titleRight{
		justify-content: flex-end !important;
	}	
}

</style>
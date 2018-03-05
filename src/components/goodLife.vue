<template>
	<div class="mainPage" :id="menuText">
		<h2>如何過熟齡理想生活</h2>
		<div class="btnBox">
			<div class="circularBtn" v-for="(btn, index) in btnBox" @click="sendGA(index)"  @mouseenter="handle_mouseenter(index)" @mouseleave="handle_mouseleave(index)"> 
				<a :href="btn.link" target="_blank">
					<img :src="btn.img" :class="{isScale: btn.isScale}">
				</a>
				<a :href="btn.link" target="_blank">
					<p>{{btn.text}}</p>	
				</a>
			</div>						
		</div>												
	</div>	
</template>

<script>
import Bus from '../eventBus.js'
import btn4_1_a from '../assets/carousel/btn4_1_a.png'
import btn4_2_a from '../assets/carousel/btn4_2_a.png'
import btn4_3_a from '../assets/carousel/btn4_3_a.png'
import btn4_4_a from '../assets/carousel/btn4_4_a.png'

import btn4_1Hover from '../assets/carousel/btn4_1h.png'
import btn4_2Hover from '../assets/carousel/btn4_2h.png'
import btn4_3Hover from '../assets/carousel/btn4_3h.png'
import btn4_4Hover from '../assets/carousel/btn4_4h.png'

import Utils from 'udn-newmedia-utils'
export default {

  name: 'goodLife',
  props: ['menuText'],
  data () {
    return {
    	btnBox: [
    		{
    			link: 'https://health.udn.com/health/story/6039/2787328',
    			img: btn4_1_a,
    			original: btn4_1_a,
    			hover: btn4_1Hover,
    			isScale: false,
    			text: '熟齡不忌口，改善肌少症。',

    		},
    		{
    			link: 'https://health.udn.com/health/story/6006/2539407',
    			img: btn4_2_a,
    			original: btn4_2_a,
    			hover: btn4_2Hover,
    			isScale: false,
    			text: '銀髮老來俏，穿出新活力。',

    		},
    		{
    			link: 'https://health.udn.com/health/story/6631/2891895',
    			img: btn4_3_a,
    			original: btn4_3_a,
    			hover: btn4_3Hover,
    			isScale: false,
    			text: '住得好安心，居家微改造。',

    		},
    		{
    			link: 'https://health.udn.com/health/story/6631/2320977',
    			img: btn4_4_a,
    			original: btn4_4_a,
    			hover: btn4_4Hover,
    			isScale: false,
    			text: '長輩趴趴走，細節要周全。',
    		}
    	]
    }
  },
  methods: {
  	handle_mouseenter: function(i) {
  		console.log('enter')
  		this.btnBox[i].img = this.btnBox[i].hover
  		this.btnBox[i].isScale = true
  	},
  	handle_mouseleave: function(i) {
  		console.log('leave')
  		this.btnBox[i].img = this.btnBox[i].original
  		this.btnBox[i].isScale = false
  	},
    handle_Emit: function() {
      const self = this
      Bus.$emit('emitHeadbarTitle', {
        title: self.menuText
      })
    },
    sendGA: function(i) {
    	const self = this
        ga("send", {
            "hitType": "event",
            "eventCategory": "超連結",
            "eventAction": "click",
            "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + self.btnBox[i].link + "] ["+ self.btnBox[i].text +"]"
        });   	
    }
  },
  mounted() {
  	this.handle_Emit()
  }
}
</script>

<style lang="scss" scoped>
h2{
	position: relative;
	z-index: 30;
	margin-right: auto;
	margin-left: auto;
	margin-bottom: 20px;
	text-align: left;
	font-size: 36px;
	line-height: 1.5;
	border-bottom: 2px solid orange;
	font-weight: bold;
	color: #343434;
	// text-shadow: 0 0px 18px rgba(48,48,48,1);
}
p{
	text-align: center;
	margin: 0 auto;
	width: 100%;
	font-size: 18px;
	line-height: 32px;
	padding: 0 15px;
}
p > br {
	ling-height: 36px;
}
.mainPage{
	position: relative;
	width: 100%;
	display: flex;
	flex-direction: column;
	padding: 0 15px;
	background-color: #f6f5f5;
}
.btnBox{
	flex-shrink: 0;
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
}
.circularBtn{
	flex-shrink: 0;
	position: relative;
	top: 0;
	left: 0;
	width: 40%;
	height: 40%;
	cursor: pointer;
	margin-bottom: 20px;
	img{
		width: 100%;
		max-height: 100%;
		margin-bottom: 15px;
		transition: 166ms ease-out;
	}
	a{
		text-decoration: none;
		color: #343434;
	}
}
.isScale{
	transform: scale(1.1);
}
@media screen and (min-width: 768px) and (max-width: 1023px){
	.mainPage{
		padding: 50px;
	}
	.btnBox{
		max-width: 880px;
	}
	.slideItem{
		img{
			width: 40%;
			left: 30%;			
		}
	}
	.circularBtn{
		img{
			padding: 15%;
		}
	}	
	h2{
		margin-top: 80px;
		margin-bottom: 40px;
	}
	p{
		width: 70%;
		font-size: 20px;
		line-height: 36px;
	}
	p > br {
		ling-height: 32px;
	}
}
@media screen and (min-width: 1024px) {
	h2{
		font-size: 70px;
		margin-top: 0;
		margin-bottom: 5%;
	}
	p{
		font-size: 21px;
		line-height: 1.5;
	}
	p > br {
		ling-height: 50px;
	}	
	.btnBox{
		padding: 0 10%;
	}	
	.mainPage{
		justify-content: center;
		padding-top: 0;
		height: 100vh;
	}	
	.circularBtn{
		position: relative;
		top: 0;
		left: 0;
		width: 20%;
		min-height: 60%;
		margin-top: 0;
		margin: 0 15px;
		img{
			padding: 12.5%;
		}
	}	
}	
</style>
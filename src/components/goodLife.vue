<template>
	<div class="mainPage" :id="menuText">
		<h2>如何過熟齡理想生活</h2>
		<div class="btnBox">
			<div class="circularBtn" v-for="(btn, index) in btnBox" @click="sendGA(index)">
				<a :href="btn.link" target="_blank"></a>
				<img :src="btn.img">
				<p>{{btn.text}}</p>
			</div>						
		</div>												
	</div>	
</template>

<script>
import Bus from '../eventBus.js'
import btn4_1 from '../assets/carousel/btn4_1.png'
import btn4_2 from '../assets/carousel/btn4_2.png'
import btn4_3 from '../assets/carousel/btn4_3.png'
import btn4_4 from '../assets/carousel/btn4_4.png'

import Utils from 'udn-newmedia-utils'
export default {

  name: 'goodLife',
  props: ['menuText'],
  data () {
    return {
    	btnBox: [
    		{
    			link: 'https://health.udn.com/health/story/6039/2787328',
    			img: btn4_1,
    			text: '食：老了就該少吃？ 改善肌少症 你該這樣吃！'
    		},
    		{
    			link: 'https://health.udn.com/health/story/6039/2787328',
    			img: btn4_2,
    			text: '衣：「老年定義，我說了算！」解放年齡 老來俏白髮潮'
    		},
    		{
    			link: 'https://health.udn.com/health/story/6039/2787328',
    			img: btn4_3,
    			text: '住：花大錢才有安全？專家：重點改造就有效果'
    		},
    		{
    			link: 'https://health.udn.com/health/story/6039/2787328',
    			img: btn4_4,
    			text: '行：帶長輩趴趴走 細節打理要周全'
    		}
    	]
    }
  },
  methods: {
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
	color: #fff;
	text-shadow: 0 0px 18px rgba(48,48,48,1);
}
p{
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
	}
	a{
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
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
		font-size: 20px;
		line-height: 36px;
	}
	p > br {
		ling-height: 32px;
	}
}
@media screen and (min-width: 1024px) {
	h2{
		font-size: 82px;
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
			margin-bottom: 40px;
			padding: 12.5%;
		}
	}	
}	
</style>
<template>
	<div class="slideShowBox">
		<div class="prev arrowBtn" @click='prev' v-show="arrowShow">
			<i class="glyphicon glyphicon-menu-left fa-3x" aria-hidden="true"></i>			
		</div>
		<div class="next arrowBtn" @click='next' v-show="arrowShow">
			<i class="glyphicon glyphicon-menu-right fa-3x" aria-hidden="true"></i>
		</div>
		<ul class='slideShow' :style="{transform: 'translateX('+ pageCount * -100 +'%)'}" :class="{forTransform: isTrans}"
			@transitionend='circleSlide'>
			<li class="mainPage">
				<h2>{{title}}</h2>
				<div class="btnBox">
					<div class="circularBtn" @click='moveToPage(1)'>
						<img src="../assets/circularbutton.png">
						<p>食：老了就該少吃？ 改善肌少症 你該這樣吃！</p>
					</div>
					<div class="circularBtn" @click='moveToPage(2)'>
						<img src="../assets/circularbutton.png">
						<p>衣：「老年定義，我說了算！」解放年齡 老來俏白髮潮</p>
					</div>
					<div class="circularBtn" @click='moveToPage(3)'>
						<img src="../assets/circularbutton.png">
						<p>住：花大錢才有安全？專家：重點改造就有效果</p>
					</div>
					<div class="circularBtn" @click='moveToPage(4)'>
						<img src="../assets/circularbutton.png">
						<p>行：帶長輩趴趴走 細節打理要周全</p>
					</div>					
				</div>												
			</li>
			<li class="slideItem" :style="{backgroundImage: 'url('+ srcRWD(bg1, bgWeb1) +')'}">
				<img src="../assets/circletitle.png">
				<div class='videoContainer' v-if='isVideo1'>
					<video :src="srcRWD(src1, srcWeb1)" controls preload="metadata" playsinline ref='video_1' @click='handle_video($refs.video_1)'></video>
				</div>
			</li>
			<li class="slideItem" :style="{backgroundImage: 'url('+ srcRWD(bg2, bgWeb2) +')'}">
				<img src="../assets/circletitle.png">
				<div class='videoContainer' v-if='isVideo2'>
					<video :src="srcRWD(src2, srcWeb2)" controls preload="metadata" playsinline ref='video_2' @click='handle_video($refs.video_2)'></video>
				</div>				
			</li>
			<li class="slideItem" :style="{backgroundImage: 'url('+ srcRWD(bg3, bgWeb3) +')'}">
				<img src="../assets/circletitle.png">
				<div class='videoContainer' v-if='isVideo3'>
					<video :src="srcRWD(src3, srcWeb3)" controls preload="metadata" playsinline ref='video_3' @click='handle_video($refs.video_3)'></video>
				</div>				
			</li>
			<li class="slideItem" :style="{backgroundImage: 'url('+ srcRWD(bg4, bgWeb4) +')'}">
				<img src="../assets/circletitle.png">
				<div class='videoContainer' v-if='isVideo4'>
					<video :src="srcRWD(src4, srcWeb4)" controls preload="metadata" playsinline ref='video_4' @click='handle_video($refs.video_4)'></video>
				</div>				
			</li>
			<li class="mainPage">
				<h2>{{title}}</h2>
				<div class="btnBox">
					<div class="circularBtn" @click='moveToPage(1)'>
						<img src="../assets/circularbutton.png">
						<p>xXXXXXXXXXXXXXXXXXXXXXXX</p>
					</div>
					<div class="circularBtn" @click='moveToPage(2)'>
						<img src="../assets/circularbutton.png">
						<p>x</p>
					</div>
					<div class="circularBtn" @click='moveToPage(3)'>
						<img src="../assets/circularbutton.png">
						<p>x</p>
					</div>
					<div class="circularBtn" @click='moveToPage(4)'>
						<img src="../assets/circularbutton.png">
						<p>x</p>
					</div>					
				</div>
			</li>			
		</ul>
	</div>
</template>

<script>
import _throttle from 'lodash.throttle'
import EmbededVideo from './EmbededVideo.vue'
import video from '../assets/oldmanvideo2_30s.mp4'

export default {

  name: 'Carousel',
  components:{
  	EmbededVideo
  },
  props: ['src1', 'srcWeb1', 'src2', 'srcWeb2', 'src3', 'srcWeb3', 'src4', 'srcWeb4', 'bg1', 'bgWeb1', 'bg2', 'bgWeb2', 'bg3', 'bgWeb3', 'bg4', 'bgWeb4', 'title'],
  data () {
    return {
    	pageCount: 0,
    	isTrans: true,
    	testVideo: video,
    	isVideo1: false,
    	isVideo2: false,
    	isVideo3: false,
    	isVideo4: false,
    }
  },
  computed: {
  	arrowShow: function() {
  		if(this.pageCount === 0 || this.pageCount === 5) {
  			return false
  		}
  		else {
  			return true
  		}
  	}
  },
  methods: {
  	handle_video: function(obj) {
  		if(obj.paused === true) {
  			obj.play()	
  		}
  		else {
  			obj.pause()
  		}
  	},
  	stop_video: function() {
  		const video = document.getElementsByTagName('video')
  		for(let i = 0; i < video.length; i++){
  			video[i].pause()
  		}
  	},
  	circleSlide: function() {
  		if(this.pageCount === 5) {
  			this.isTrans = false
  			this.pageCount = 0
  		}
  		// else if(this.pageCount === 0) {
  		// 	this.isTrans = false
  		// 	this.pageCount = 5
  		// }
  	},
  	next: _throttle(function() {
  		if(this.pageCount < 5) {
  			this.isTrans = true
  			this.pageCount ++
  			this.stop_video()
  		}
  	}, 666, {'leading': true, 'trailing': false}),
  	prev: _throttle(function() {
  		if(this.pageCount > 0) {
  			this.isTrans = true
  			this.pageCount -- 
  			this.stop_video()
  		}
  	}, 666, {'leading': true, 'trailing': false}),
  	moveToPage: function(count) {
  		this.isTrans = true
  		this.pageCount = count
  	},
	srcRWD: function(mob, pc) {
		if(window.innerWidth < 1024){
 			return mob
		}
		else {
			return pc
		}				
	},
	isVideo: function(mob, pc) {
		if(mob !== undefined && pc !== undefined){
			return true
		}
		else {
			return false
		}
	}
  },
  created() {
 	
  },
  mounted() {
		this.isVideo1 = this.isVideo(this.src1, this.srcWeb1)
		this.isVideo2 = this.isVideo(this.src2, this.srcWeb2)
		this.isVideo3 = this.isVideo(this.src3, this.srcWeb3)
		this.isVideo4 = this.isVideo(this.src4, this.srcWeb4) 
  }
}
</script>

<style lang="scss" scoped>
.slideShowBox{
	position: relative;
	top: 0;
	left: 0;
	width: 100%;
	height: 100vh;
	overflow: hidden;
}
.arrowBtn{
	position: absolute;
	z-index: 9999;
	height: 50px;
	margin-top: -25px;
	color: #fff;
	cursor: pointer;
	text-shadow: 2px 1px rgba(48,48,48,1);
	animation: bounceIn 444ms ease-in-out;
}
.prev{
	top: 50%;
	left: 0;
	margin-left: 5px;
}
.next{
	top: 50%;
	right: 0;
	margin-right: 5px;
}
.slideShow{
	position: relative;
	width: 100%;
	height: 100%;
	list-style: none;
	padding: 0;
	display: flex;
	align-items: center;
	tranform: translate(0, 0);
	li{
		flex-shrink: 0;
		position: relative;
		width: 100%;
		height: 100%;
		background-size: cover;
		background-repeat: no-repeat;
		background-position: center center;
	}
	.mainPage{
		display: flex;
		flex-direction: column;
		padding: 0 15px;
		background-color: #f6f5f5;
	}
}
.slideItem{
	position: relative;
	width: 100%;
	height: 100%;
	overflow: hidden;
	background-size: cover;
	background-position: center center;
	background-repeat: no-repeat;
	img{
		position: absolute;
		z-index: 30;
		left: 20%;
		bottom: 50px;
		width: 60%;
		pointer-events: none;
	}
	video{
		width: 100%;
		height: 100%;
		object-fit: fill;
		cursor: pointer;
	}
}
.forTransform{
	transition-property: transform;
	transition-duration: 666ms;
	transition-timing-function: ease-in-out;
}
.btnBox{
	display: flex;
	height: 100%;
	flex-wrap: wrap;
	justify-content: space-between;
}
.circularBtn{
	position: relative;
	top: 0;
	left: 0;
	width: 40%;
	height: 40%;
	cursor: pointer;
	img{
		width: 100%;
		max-height: 100%;
		margin-bottom: 15px;
	}
}
.videoContainer{
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}
h2{
	position: relative;
	z-index: 30;
	margin-right: auto;
	margin-left: auto;
	margin-bottom: 15px;
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
@media screen and (min-width: 768px) and (max-width: 1023px){
	.btnBox{
		max-width: 880px;
	}
	.slideItem{
		img{
			width: 40%;
			left: 30%;			
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
		margin-top: 100px;
		font-size: 92px;
		margin-bottom: 80px;
	}
	p{
		font-size: 21px;
		line-height: 1.5;
	}
	p > br {
		ling-height: 50px;
	}
	.btnBox{
		width: 80%;
		margin: 0 auto;
	}	
	.slideShow{
		.mainPage{
			justify-content: center;
			padding-top: 0;
		}
	}.slideItem{
		img{
			top: 20px;
			left: 100%;
			width: 300px;
			margin-left: -320px;
		}
	}
	.circularBtn{
		position: relative;
		top: 0;
		left: 0;
		width: 15%;
		min-height: 50%;
		margin-top: 0;
		margin: 0 15px;
	}	
}
@keyframes bounceIn {
	0%{
		transform: scale(1);
		opacity: 0;
	}
	42%{
		transform: scale(1.1);
		opacity: 1;
	}
	100%{
		transform: scale(1);
		opacity: 1;
	}
}
</style>
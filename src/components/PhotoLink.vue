<template>
	<div class="PhotoLinkWrapper" :id="menuText">
		<h2 class="title">{{title}}</h2>
		<div class="photoContainer">
			<div class="photolink" v-for="(person, index) in people" 
				 :style="{backgroundImage: 'url('+ person.img +')'}" :class="{isActive: person.isActive}">
				<a :href="person.href" target="_blank"></a>
				<div class="imgTitle">
					<h3 class='mainTitle'>{{person.mainTitle}}</h3>
					<h3 class="subTitle"><span v-html="person.subTitle"></span></h3>
				</div>	
			</div>
			<div class="prev arrowBtn hidden-lg hidden-md" @click='handle_clickPrev'>
				<i class="glyphicon glyphicon-menu-left fa-3x" aria-hidden="true"></i>
			</div>
			<div class="next arrowBtn hidden-lg hidden-md" @click='handle_clickNext'>
				<i class="glyphicon glyphicon-menu-right fa-3x" aria-hidden="true"></i>
			</div>									
		</div>
	</div>
</template>

<script>
import Bus from '../eventBus.js'
import Utils from 'udn-newmedia-utils'
export default {

  name: 'PhotoLink',
  props: ['title', 'img1', 'href1', 'img2', 'href2', 'img3', 'href3', 'imgStart', 'mainTitle1', 'subTitle1', 'mainTitle2', 'subTitle2', 'mainTitle3', 'subTitle3', 'menuText'],
  data () {
    return {
    	people:[
    		{
    			'img': null,
    			'href': null,
    			'mainTitle': null,
    			'subTitle': null,
    			'isActive': true,
    			'isSec': false
    		},
    		{
    			'img': null,
    			'href': null,
    			'mainTitle': null,
    			'subTitle': null,
    			'isActive': false,
    			'isSec': false
    		},
    		{
    			'img': null,
    			'href': null,
    			'mainTitle': null,
    			'subTitle': null,
    			'isActive': false,
    			'isSec': true
    		}    		    		
    	]
    }
  },
  computed: {

  },	
  methods: {
    handle_Emit: function() {
      const self = this
      Bus.$emit('emitHeadbarTitle', {
        title: self.menuText
      })
    },
    sendGA: function(i){
    	const self = this
        ga("send", {
            "hitType": "event",
            "eventCategory": "超連結",
            "eventAction": "click",
            "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + self.people[i].href + "] ["+ self.people[i].mainTitle +"]"
        });   	    	
        // console.log("[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + self.people[i].href + "] ["+ self.people[i].mainTitle +"]")
    },
  	get_Index: function() {
  		const peopleLength = this.people.length
  		for(let i = 0; i < peopleLength; i++){
  			if(this.people[i].isActive === true) {
  				return i
  			}
  		}
  	},
  	handle_click: function(i) {
  		if(window.innerWidth >= 1024) {
  			for(let i = 0; i < this.people.length; i++){
  				this.people[i].isActive = false
  			}
  			this.people[i].isActive = true
  		}
  	},
  	handle_clickNext: function() {
  		const peopleLength = this.people.length
  		const getIndex = this.get_Index()
  		this.people[getIndex].isActive = false
  		if(this.people[getIndex + 1] !== undefined){	  		
	  		this.people[getIndex + 1].isActive = true
  		} else {
  			this.people[0].isActive = true
  		}
  	},
  	handle_clickPrev: function() {
  		const peopleLength = this.people.length
		const getIndex = this.get_Index()
  		this.people[getIndex].isActive = false
  		if(this.people[getIndex - 1] !== undefined){	  		
	  		this.people[getIndex - 1].isActive = true
  		} else {
  			this.people[peopleLength - 1].isActive = true
  		}
  	},
  	layoutRWD: function() {
  		if(window.innerWidth >= 1024){
  			return 30
  		} else {
  			return 0
  		}
  	},
  	handle_resize: function() {
  		this.$forceUpdate()
  	}
  },
  created () {
    window.addEventListener('resize', this.handle_resize)
    this.people[0].img = this.$props.img1
    this.people[1].img = this.$props.img2
    this.people[2].img = this.$props.img3
    this.people[0].href = this.$props.href1
    this.people[1].href = this.$props.href2
    this.people[2].href = this.$props.href3
    this.people[0].mainTitle = this.$props.mainTitle1
    this.people[1].mainTitle = this.$props.mainTitle2
    this.people[2].mainTitle = this.$props.mainTitle3
    this.people[0].subTitle = this.$props.subTitle1
    this.people[1].subTitle = this.$props.subTitle2
    this.people[2].subTitle = this.$props.subTitle3
    if(this.$props.imgStart === 'right'){
    	this.people[0].isActive = false
    	this.people[2].isActive = true
    }
  },
  beforeDestroy () {
  	window.removeEventListener('resize', this.handle_resize)
  },
  mounted() {
  	this.handle_Emit()
  }
}
</script>

<style lang="scss" scoped>
.PhotoLinkWrapper{
	position: relative;
	z-index: 100;
	width: 100%;
	height: 100vh;
	background-color: #f6f5f5;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-around;
	// overflow: hidden;
	h2{
		position: relative;
		z-index: 30;
		text-align: left;
		font-size: 42px;
		line-height: 1.5;
		border-bottom: 2px solid orange;
		font-weight: bold;
		color: #343434;
		margin-top: 60px;
	}
}
.photoContainer{
	position: relative;
	z-index: 0;
	width: 100%;
	height: 80%;
	display: flex;
	align-items: center;
	justify-content: space-around;
}
.photolink{
	position: absolute;
	z-index: 0;
	top: 0;
	left: 0;
	height: 100%;
	width: 100%;
	padding: 15px 15px 15px 15px;
	background-clip: content-box;
	background-size: cover;
	background-position: center top;
	a{
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
}
.isActive{
	z-index: 10 !important;
}
.arrowBtn{
	position: absolute;
	z-index: 9999;
	height: 50px;
	margin-top: -25px;
	color: #fff;
	cursor: pointer;
	// text-shadow: 2px 4px rgba(48,48,48,0.3);
}
.prev{
	top: 50%;
	left: 0;
	margin-left: 15px;
}
.next{
	top: 50%;
	right: 0;
	margin-right: 15px;
}
.imgTitle{
	position: absolute;
	z-index: 0;
	left: 15px;
	bottom: 5%;
	padding-left: 15px;
	pointer-events: none;
}
.mainTitle{
    font-size: 36px;
    font-weight: bold;
    letter-spacing: -1px;
    color: #FFFFFF;
    line-height: 1.1;
    text-shadow: 0 0px 18px rgba(48,48,48,1);
    margin: 0;	
}
.subTitle{
	width: 100%;
  font-size: 30px;
  text-align: left;
  color: #FFFFFF;
  margin-top: 5px;
  margin-bottom: 0;
  text-shadow: 0 0px 18px rgba(48,48,48,1);
}
@media screen and (min-width: 768px) and (max-width: 1024px) {
	.mainTitle{
		font-size: 30px;
	}
	.subTitle{
		font-size: 30px;
	}
}
@media screen and (min-width: 1024px) {
	.PhotoLinkWrapper{
		h2{
			width: auto;
			font-size: 50px;
		}
	}
	.photoContainer{
		justify-content: center;
	}
	.photolink{
		position: relative;
		width: 30%;
	}
}
@keyframes fadeIn {
	from{
		opacity: 0;
	}
	to{
		opacity: 1;
	}
}
</style>
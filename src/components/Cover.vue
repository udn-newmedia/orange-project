<template>
  <div :id="menuText" class="cover" :style="{backgroundImage: 'url(' + bgRWD() + ')'}" :class="{top: top, bottom: bottom, aligncenter: aligncenter}">
    <div id="title-contain" :style="{backgroundColor: boxColor}">
      <h1 :class="{theShadow: !noShadow}" :style="{color: color}">{{title}}</h1>
      <div id="sub-title" :class="{theShadow: !noShadow}" :style="{color: color}">{{subtitle}}</div>
      <slot></slot>
    </div>
    <slot name="anchor"></slot>
  </div>
</template>

<script>
import Bus from '../eventBus.js'
export default {
    name: 'Cover',
    props: ['title', 'subtitle', 'bg', 'bgweb', "position", "noShadow", "boxColor", "color", "menuText"],
    data: function(){
        return{
            aligncenter: false,
            top: false,
            bottom: false,
        }
    },
    created: function(){
        window.addEventListener('resize', () => {
            this.$forceUpdate()
        })
        if(this.position == 'top'){
            this.top = true
        }
        if(this.position == 'bottom'){
            this.bottom = true
        }
        if(this.position == 'middle'){
            this.aligncenter = true
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
      handle_Emit: function() {
        const self = this
        Bus.$emit('emitHeadbarTitle', {
          title: self.menuText
        })
      },
    },
    mounted: function() {
      this.handle_Emit()
    }
}
</script>

<style lang="scss" scoped>
    #title-contain{
      position: relative;
      width: 45%;
      padding: 20px;
      max-width: 550px;
    }
    .cover{
        position: relative;
        height: 100%;
        background-position: center center;
        background-repeat: no-repeat;
        background-size: cover;
        overflow: hidden;
        display: flex;
        flex-direction: column;
        justify-content: center;
        padding: 12% 8%;
        a{
          text-decoration: none;
        }
    }
    .cover.top{
        justify-content: flex-start;
    }
    .cover.bottom{
        justify-content: flex-end;
    }
    .aligncenter{
        align-items: center;
    }
    .theShadow{
        text-shadow: 0 0px 18px rgba(48,48,48,1);
    }
    .arrow_box{
      position: absolute;
      right: 20px;
      bottom: 20px;
      color: #000;
    }
    h1{
        font-size: 55px;
        font-weight: bold;
        letter-spacing: -1px;
        color: #FFFFFF;
        line-height: 1.1;
        /* text-shadow: 0 0px 18px rgba(48,48,48,1); */
        margin: 0;
    }
    #sub-title{
        font-size: 55px;
        color: #FFFFFF;
    }

    @media screen and (max-width: 767px) {
        h1{
            font-size: 40px;
        }
        #sub-title{
            font-size: 25px;
        }
        .cover{
            padding: 30% 0;
        }
        #title-contain{
          width: 90%;
          margin: 0 auto;
        }
    }

    @media screen and (min-width: 768px) and (max-width: 1024px) {
        h1{
            font-size: 45px;
        }
        #sub-title{
            font-size: 30px;
        }
        .cover{
            padding: 30% 0;
        }
        #title-contain{
          width: 60%;
          padding: 0 100px;
        }
    }

</style>

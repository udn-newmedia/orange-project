<template>
  <div id="app">
    <Indicator color='#bf2923'></Indicator>
    <HeadBar 
      MenuSlideFrom='right' 
      color="#000" 
      background-color="#fff" 
      href='https://udn.com/upf/newmedia/2018_data/orange-project/index.html'>
      <a href="https://udn.com/upf/newmedia/2018_data/British-Council_2/" target="_target">
        大人英語課
      </a>
    </HeadBar>
    <AddMenuTitle
      menu-text="多值人生">
    </AddMenuTitle>
    <Cover 
      title="" 
      subtitle="" 
      position='top' 
      style="background-color: #000" 
      :bg='cover_new_1_m' 
      :bgweb="cover_new_1"
      noShadow="false" 
      color="#fff" 
      useArrow="true">
      <div class="title-wrapper">
        <div class="vertical-title-wrapper-left" style="background-color: #fff600">
          <p class="vertical-title-left">
            熟齡３大關鍵力 &nbsp&nbsp            
          </p>
        </div>
        <div class="vertical-title-wrapper-right" style="background-color: #fff600">
          <p class="vertical-title-right">
            開啟多值人生 &nbsp&nbsp
          </p>
        </div>
      </div>
    </Cover>

    <Content background-color="#fff" style="padding-bottom: 0 !important" class="cusContent">
      <Share href="https://udn.com/upf/newmedia/2018_data/orange-project/index.html"></Share>
      <p><br/></p>
      <p>面對50歲以後的人生，你打算怎麼過？在兼顧家庭與事業後，人生達到相對巔峰。從現在開始，生活重心不再只有工作，而是用更開闊的心、多方嘗試，發掘潛在可能，實現未完成的理想，退休不再是唯一選擇。</p>
      <p><br/></p>
      <p>在探索新生活的同時，不僅自我實現、認同，也能創造對他人有意義的價值，開啟豐富的多值人生。</p>
      <p><br/></p>
      <p><br/></p>
    </Content>
    <!-- <DFPads></DFPads> -->

    <ReadMore2 
      href="https://udn.com/upf/newmedia/2018_data/orange-project/mature/shen.html"
      menu-text="沈春華勇敢歸零"
      position='right' 
      title-color="#fff" 
      fontColor="#000" 
      useReadMore='yes'
      :bg='slash_new_1_m' 
      :bgweb="slash_new_1" 
      title="行經谷底 看見另一道風景" 
      subtitle="沈春華：活得精彩 是給兒女的重要資產" 
      useShadow="true"
      style="background-size: contain; background-color: #eeeeee;">
    </ReadMore2>
    <ReadMore2 
      href="https://udn.com/upf/newmedia/2018_data/orange-project/mature/wu.html"
      menu-text="吳明珠熱愛工作"
      position='left' 
      title-color="#fff" 
      fontColor="#000" 
      useReadMore='yes'
      :bg='slash_new_2_m' 
      :bgweb="slash_new_2" 
      title="快60歲美魔女 逆齡生長像少女" 
      subtitle="吳明珠：愛吃愛玩愛工作 退休還早咧" 
      useShadow="true"
      style="background-size: contain; background-color: #ffffff;">
    </ReadMore2>
    <ReadMore2 
      href="https://udn.com/upf/newmedia/2018_data/orange-project/mature/huang.html"
      menu-text="熟齡3大關鍵力"
      position='right' 
      title-color="#fff" 
      fontColor="#000" 
      useReadMore='yes'
      :bg='slash_new_3_m' 
      :bgweb="slash_new_3" 
      title="掌握３大關鍵" 
      subtitle="黃培直：開啟橘色世代的多值人生" 
      useShadow="true"
      style="background-size: contain; background-color: #eeeeee;">
    </ReadMore2>
    <div id="slash"></div>
    <Cover 
      title="斜槓大人" 
      subtitle="褚士瑩 ╳ 劉軒" 
      position='bottom' 
      style="background-color: #000" 
      :bg='slash_1_m' 
      :bgweb="slash_1"
      noShadow="false" color="#fff" useArrow="true">
      <Share href='https://udn.com/upf/newmedia/2018_data/orange-project/index.html'></Share>
    </Cover>
    <Content background-color="#E6E6E6" style="padding-bottom: 0 !important" class="cusContent">
      <p>全球年輕人瘋斜槓人生，不滿於單一工作做到老。但斜槓是年輕人的專利嗎？斜槓需要幾分的本錢、幾分的勇敢。台灣的斜槓標竿人物褚士瑩、劉軒都說，需要的是坦誠面對自己，什麼樣的人生才不後悔？</p>
    </Content>
    <ReadMore2 
      href="https://udn.com/upf/newmedia/2018_data/slash/talk.html"
      menu-text="斜槓大人"
      position='right' 
      title-color="#fff" 
      fontColor="#000" 
      useReadMore='yes'
      :bg='slash_0_m' 
      :bgweb="slash_0" 
      title="不必一份工作到老" 
      subtitle="斜槓贏回人生主導權" 
      useShadow="true"
      style="background-size: contain;background-color: #E6E6E6;">
    </ReadMore2>
    <Banner :src="Banner_1" :srcWeb="Banner_1_pc" manufacture="臺中化妝品展" href="http://bit.ly/2GuGODE" expire="2018/06/05"></Banner>
    <ReadMore2 
      href="https://udn.com/upf/newmedia/2018_data/slash/chu.html"
      position='left' 
      title-color="#fff" 
      fontColor="#000" 
      useReadMore='yes'
      :bg='slash_2_m' 
      :bgweb="slash_2" 
      title="人生不想單一" 
      subtitle="褚士瑩：你需要勇氣與練習" 
      useShadow="true"
      style="background-size: contain">
    </ReadMore2>
    <ReadMore2 
      href="https://udn.com/upf/newmedia/2018_data/slash/liu.html"
      position='right' 
      title-color="#fff" 
      fontColor="#000" 
      useReadMore='yes'
      :bg='slash_3_m' 
      :bgweb="slash_3" 
      title="隔行不隔山" 
      subtitle="劉軒：用同理心穿別人的鞋走 一哩路" 
      useShadow="true"
      style="background-size: contain; background-color: #55CAF5">
    </ReadMore2>
    <Cover 
      title="回甘大人" 
      subtitle="熟齡的新生活學" 
      position='bottom' 
      style="background-color: #000" 
      :bg='cover_1_m' 
      :bgweb="cover_1" 
      menuText="回甘大人">
      <div id="relife" slot="anchor"></div>
    </Cover>
    <ReadMore2 position='right' href="https://theme.udn.com/theme/story/6774/2994070" title-color="rgba(99,186,134,0.8)" fontColor="#fff" useReadMore='yes'
              :bg='cover_3_m' :bgweb="cover_3" title="橘色世代滑出存在感" subtitle="渴望「向下認同」"></ReadMore2>
    <ReadMore2 position='left' title-color="rgba(99,186,134,0.8)" href="https://theme.udn.com/theme/story/6774/2994101" useReadMore='yes'
              :bg='cover_2_m' :bgweb="cover_2" title="練肌肉、穿韓版服飾 " subtitle="不服老的回甘人生"></ReadMore2>
    <PhotoLink title="名人的理想生活" imgStart="left"
    :img1="people_1" mainTitle1='李昂'   subTitle1='老後生活<br/>你儲存愛情了嗎?'    href1='https://theme.udn.com/theme/story/6774/2992791'
    :img2='people_2' mainTitle2='岑永康' subTitle2='空巢期到南美洲<br/>來場拉丁式冒險' href2='https://theme.udn.com/theme/story/6774/2992969'
    :img3='people_3' mainTitle3='陳建仁' subTitle3='遠離「失重感」<br/>退休也要有夢' href3='https://theme.udn.com/theme/story/6774/2994560'></PhotoLink>
    <GoodLife></GoodLife>
    <ReadMore2 position='left' title-color="rgba(99,186,134,0.8)" href="https://www.youtube.com/watch?v=IiRwmOCUVLQ" useReadMore='yes'
              :src="video" :srcWeb="videoPC" title="大人young " subtitle="快時尚優雅穿搭術"></ReadMore2>
    <ReadMore2 class="cusBanner" position='right' href="https://www.youtube.com/watch?v=r16Mke1jUCs&feature=youtu.be" title-color="rgba(99,186,134,0.8)" font-color="#fff" useReadMore='yes' :bg='huananRelate' :bgweb="huananCover" title="華南銀行" subtitle="守護你的初衷"></ReadMore2>
    <Content background-color="#FFFFFF">
        <p><br/></p>
        <Share href="https://udn.com/upf/newmedia/2018_data/orange-project/index.html"></Share>
        <Logo></Logo>
        <p><br/></p>
        <Editor>
            <div>製作人：吳思萍、林秀姿、蔡佩蓉、盧巧梅、蘇彥菱</div>
            <div>視覺設計：張心慈、許瑋琳</div>
            <div>網頁製作：廖克樸、楊若榆</div>
            <div>影音：張心慈、蘇士堯、舒懷緯、許瑋琳</div>
            <div>攝影：林俊良、徐兆玄、陳柏亨、侯永全</div>
            <div>圖片來源：<a href="https://tw.123rf.com/" style="color: gray;text-decoration: none" target="_blank">123RF</a></div>
            <div>監製：董谷音、蔡幸怡、潘如瑩、陳曼薇</div>
            <div>議題行銷：張乃文、陳欣媛、蔡嘉棋、王敏霏</div>
            <div>2018.08.28</div>
        </Editor>
        <p><br/></p>
        <Relate title="延伸閱讀" color="#363434"
            href1="https://www.aptg.com.tw/event/1803/HipHop/?&utm_source=udn&utm_medium=300x250&utm_campaign=201803_333onlineshop" :img1="AsiaBanner" text1="亞太門市 1塊打電話上網吃到飽"
            href2="https://goo.gl/PEyrRp" :img2="huananRelate" text2="華南銀行 守護你的初衷"
            href3="https://health.udn.com/health/story/6006/2813024" :img3="relate_1" text3="給智慧銀髮族：早安圖、幸運信不要再傳啦"
            href4="https://udn.com/news/story/7241/2975251" :img4="relate_4" text4="春節橘色高齡族群商機 「宅經濟」最夯">
        </Relate>
        <p><br/></p>
        <Fb-Comment href="https://udn.com/upf/newmedia/2018_data/orange-project/index.html"></Fb-Comment>
    </Content>
    <Foot background-color="#FFFFFF"></Foot>
  </div>
</template>

<script>
import {Indicator, Share, Content, Foot, FbComment, Editor} from 'udn-newmedia-vue-components'
import Relate from './components/Relate.vue'
import AddMenuTitle from './components/AddMenuTitle.vue'
import Banner from './components/banner.vue'
import GoodLife from './components/goodLife.vue'
import Cover from './components/Cover.vue'
import HeadBar from './components/HeadBar.vue'
import ReadMore from './components/ReadMore.vue'
import ReadMore2 from './components/ReadMore2.vue'
import PhotoLink from './components/PhotoLink.vue'
import DFPads from './components/DFPads'
import Logo from './components/Logo.vue'

import people_1 from './assets/people_1.jpg'
import people_2 from './assets/people_2.jpg'
import people_3 from './assets/people_3.jpg'

import slash_0 from './assets/slash/pc/0502update_web_talk-Cover.jpg'
import slash_1 from './assets/slash/pc/web_img_1.jpg'
import slash_2 from './assets/slash/pc/web_img_2.jpg'
import slash_3 from './assets/slash/pc/web_img_3.jpg'

import slash_0_m from './assets/slash/0502update_phone-talk-Cover.jpg'
import slash_1_m from './assets/slash/slash_1.jpg'
import slash_2_m from './assets/slash/slash_2.jpg'
import slash_3_m from './assets/slash/slash_3.jpg'


import slash_new_1 from './assets/mature/w1.jpg'
import slash_new_2 from './assets/mature/w2.jpg'
import slash_new_3 from './assets/mature/w3.jpg'
import slash_new_1_m from './assets/mature/m1.jpg'
import slash_new_2_m from './assets/mature/m2.jpg'
import slash_new_3_m from './assets/mature/m3.jpg'
import cover_new_1 from './assets/mature/mature_wbg.jpg'
import cover_new_1_m from './assets/mature/mature_mbg.jpg'

import cover_1 from './assets/slash/pc/web_img_4.jpg'
import cover_2 from './assets/cover_2.jpg'
import cover_3 from './assets/cover_3.jpg'
import cover_4 from './assets/cover_4.jpg'

import cover_1_m from './assets/slash/slash_4.jpg'
import cover_2_m from './assets/cover_2_m.jpg'
import cover_3_m from './assets/cover_3_m.jpg'
import cover_4_m from './assets/cover_4_m.jpg'

import relate_1 from './assets/relate_1.jpg'
import relate_2 from './assets/relate_2.jpg'
import AsiaBanner from './assets/asia_banner.jpg'
import relate_4 from './assets/relate_4.jpg'

import huananCover from './assets/bank_ad/AD_.jpg'
import huananRelate from './assets/bank_ad/huanan_relate_ad.jpg'

// import ImgBanner from './assets/banner.jpg'

import video from './assets/oldvideo_mob.mp4'
import video_pc from './assets/oldmanvideo2_30s.mp4'

import Banner_1 from './assets/banner/Banner_mobile02.jpg'
import Banner_1_pc from './assets/banner/Banner_web02.jpg'

export default {
  name: 'App',
  components: {
    AddMenuTitle,
    Banner,
    Cover,
    Content,
    DFPads,
    HeadBar,
    Editor,
    GoodLife,
    Logo,
    FbComment,
    Foot,
    Indicator,
    ReadMore,
    ReadMore2,
    Relate,
    Share,
    PhotoLink
  },
  data() {
    return{
      // ImgBanner: ImgBanner,
      Banner_1: Banner_1,
      Banner_1_pc: Banner_1_pc,
      people_1: people_1,
      people_2: people_2,
      people_3: people_3,
      slash_0: slash_0,
      slash_1: slash_1,
      slash_2: slash_2,
      slash_3: slash_3,
      slash_0_m: slash_0_m,
      slash_1_m: slash_1_m,
      slash_2_m: slash_2_m,
      slash_3_m: slash_3_m,

      slash_new_1: slash_new_1,
      slash_new_2: slash_new_2,
      slash_new_3: slash_new_3,
      slash_new_1_m: slash_new_1_m,
      slash_new_2_m: slash_new_2_m,
      slash_new_3_m: slash_new_3_m,
      cover_new_1: cover_new_1,
      cover_new_1_m: cover_new_1_m,
      
      cover_1: cover_1,
      cover_2: cover_2,
      cover_3: cover_3,
      cover_4: cover_4,
      cover_1_m: cover_1_m,
      cover_2_m: cover_2_m,
      cover_3_m: cover_3_m,
      cover_4_m: cover_4_m,
      relate_1: relate_1,
      relate_2: relate_2,
      AsiaBanner: AsiaBanner,
      relate_4: relate_4,
      video: video,
      videoPC: video_pc,
      
      huananCover,
      huananRelate,

      menu_title_order: ["多值人生", "熟齡３大關鍵力", "沈春華勇敢歸零", "吳明珠熱愛工作", "斜槓大人", "回甘大人", "大人英語課"]
    }
  },
  mounted: function(){
    var temp = 
    console.log($("#hbutton-contain")[0].children);
    
  }
}
</script>

<style lang="scss">
#app {
  font-size: 16px;
  line-height: 1.5;
  font-family: Arial, Microsoft JhengHei, sans-serif;
  word-wrap: break-word;
  text-align: justify;
  height: 100vh;
  width: 100%;
}
.title-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  transform: translateX(-3vw) translateY(3vh);
}
.vertical-title-wrapper-right {
  width: 42px;
  margin: 5px;
  transform: translateY(-8em);
}
.vertical-title-wrapper-left {
  width: 32px;
  margin: 5px;
  transform: translateY(-4em);
}
.vertical-title-right {
  font-size: 34px;
  line-height: 1;
  white-space:nowrap;
  color: #000;
  -webkit-writing-mode: vertical-lr;
  writing-mode: vertical-lr;
  transform: translateX(8px) translateY(10px);
}
.vertical-title-left {
  font-size: 22px;
  line-height: 1;
  white-space:nowrap;
  color: #000;
  -webkit-writing-mode: vertical-lr;
  writing-mode: vertical-lr;
  transform: translateX(8px) translateY(10px);
}
.cusBanner{
  background-size: contain !important;
  background-position: center 25% !important;
}
.cusContent{
  .container{
    padding-bottom: 0 !important;
  }
}
#relife{
  position: absolute;
  top: 0;
  left: 0;
  z-index: -100;
  background-color: transparent;
}
@media screen and (min-width: 768px) and (max-width: 1023px){
.title-wrapper {
  transform: translateX(20vw) translateY(3vh);
}
}
@media screen and (min-width: 1024px){
  .cusBanner{
    background-size: auto 100% !important;
    background-position: center 50px !important;
  }
  .title-wrapper {
    transform: translateX(37vw);
  }
  .vertical-title-wrapper-right {
    width: 5.3em;
    margin: 10px;
    transform: translateY(-8em);
  }
  .vertical-title-wrapper-left {
    width: 3.6em;
    margin: 10px;
    transform: translateY(-2em);
  }
  .vertical-title-right {
    font-size: 3.8em;
    transform: translateX(0.38em) translateY(10px);
  }
  .vertical-title-left {
    font-size: 2.6em;
    transform: translateX(0.36em) translateY(10px);
  }
}
</style>

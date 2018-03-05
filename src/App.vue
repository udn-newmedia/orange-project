<template>
  <div id="app">
    <Indicator color='#ff9a57'></Indicator>
    <HeadBar MenuSlideFrom='right' color="#fff" background-color="#ffbd6e" href='https://udn.com/upf/newmedia/2018_data/orange-project/index.html'></HeadBar>
    <Cover title="回甘大人" subtitle="熟齡的新生活學" position='bottom' style="background-color: #000" :bg='cover_1_m' :bgweb="cover_1">
      <Share href='https://udn.com/upf/newmedia/2018_data/orange-project/index.html'></Share>
    </Cover>
    <Banner background-color="#515151" :src='ImgBanner'></Banner>
    <ReadMore menu-text="找認同" position='right' href="www.facebook.com" title-color="rgba(99,186,134,0.8)" fontColor="#fff" useReadMore='yes'
              :bg='cover_3_m' :bgweb="cover_3" title="橘色世代滑出存在感" subtitle="渴望「向下認同」"></ReadMore>    
    <ReadMore menu-text="找青春" position='left' title-color="rgba(99,186,134,0.8)" href="www.facebook.com" useReadMore='yes'
              :bg='cover_2_m' :bgweb="cover_2" title="練肌肉、穿韓版服飾 " subtitle="不服老的回甘人生"></ReadMore>    
    <PhotoLink title="名人的理想生活" imgStart="left" menuText="名人樂活"
    :img1="people_1" mainTitle1='李昂'   subTitle1='老後生活你儲存愛情了嗎?'    href1='https://www.youtube.com/watch?v=bMnazmyqkqw'
    :img2='people_2' mainTitle2='岑永康' subTitle2='空巢期到南美來場拉丁式冒險' href2='https://www.youtube.com/watch?v=bMnazmyqkqw'
    :img3='people_3' mainTitle3='陳建仁' subTitle3='遠離「失重感」退休也要有夢' href3='https://goo.gl/jLpogP'></PhotoLink>
    <GoodLife menu-text="生活實踐"></GoodLife>   
    <ReadMore menu-text="Young穿搭" position='left' title-color="rgba(99,186,134,0.8)" href="https://www.youtube.com/watch?v=IiRwmOCUVLQ" useReadMore='yes'
              :src="video" :srcWeb="videoPC" title="大人young " subtitle="快時尚優雅穿搭術"></ReadMore>    
    <ReadMore menu-text="學理財" position='right' href="https://udn.com/upf/newmedia/2017_data/ideal/check.html" title-color="rgba(99,186,134,0.8)" font-color="#fff" useReadMore='yes'
              :bg='cover_4_m' :bgweb="cover_4" title="三大退休族" subtitle="達人教你理財術"></ReadMore>           
    <Content background-color="#FFFFFF">
        <p><br/></p>
        <Share href="https://udn.com/upf/newmedia/2018_data/orange-project/index.html"></Share>
        <Logo></Logo>
        <p><br/></p>
        <Editor>
            <div>製作人：吳思萍、蔡佩蓉</div>
            <div>視覺設計：呂紹齊</div>
            <div>網頁製作：廖克樸</div>
            <div>影音：呂紹齊、蘇士堯、舒懷緯</div>
            <div>攝影：侯永全、陳柏亨</div>
            <div>圖片來源：<a href="https://tw.123rf.com/" style="color: gray;text-decoration: none" target="_blank">123RF</a></div>
            <div>監製：董谷音、蔡幸怡</div>
            <div>2018.03.15</div>
        </Editor>
        <p><br/></p>
        <Relate title="延伸閱讀" color="#363434" 
            href1="https://health.udn.com/health/story/6006/2983486" :img1="relate_2" text1="退休老師寫自傳 找回心中缺角" 
            href2="https://health.udn.com/health/story/6006/2813024" :img2="relate_1" text2="給智慧銀髮族：早安圖、幸運信不要再傳啦" 
            href3="https://udn.com/news/story/6885/1686304" :img3="relate_3" text3="看準退休族消費經濟 私校搶橘色商機" 
            href4="https://udn.com/news/story/7241/2975251" :img4="relate_4" text4="春節橘色高齡族群商機 「宅經濟」最夯"> 
        </Relate>
        <p><br/></p>
        <Fb-Comment href="https://udn.com/upf/newmedia/2018_data/orange-project/index.html"></Fb-Comment>
    </Content>
    <Foot background-color="#FFFFFF"></Foot>
  </div>
</template>

<script>
import {Indicator, Share, Relate, Content, Foot, FbComment, Logo, Editor} from 'udn-newmedia-vue-components'
import Banner from './components/banner.vue'
import GoodLife from './components/goodLife.vue'
import Cover from './components/Cover.vue'
import HeadBar from './components/HeadBar.vue'
import ReadMore from './components/ReadMore.vue'
import PhotoLink from './components/PhotoLink.vue'

import people_1 from './assets/people_1.jpg'
import people_2 from './assets/people_2.jpg'
import people_3 from './assets/people_3.jpg'

import cover_1 from './assets/cover_1.jpg'
import cover_2 from './assets/cover_2.jpg'
import cover_3 from './assets/cover_3.jpg'
import cover_4 from './assets/cover_4.jpg'

import cover_1_m from './assets/cover_1_m.jpg'
import cover_2_m from './assets/cover_2_m.jpg'
import cover_3_m from './assets/cover_3_m.jpg'
import cover_4_m from './assets/cover_4_m.jpg'

import relate_1 from './assets/relate_1.jpg'
import relate_2 from './assets/relate_2.jpg'
import relate_3 from './assets/relate_3.jpg'
import relate_4 from './assets/relate_4.jpg'

import ImgBanner from './assets/banner.jpg'

import video from './assets/oldvideo_mob.mp4'
import video_pc from './assets/oldmanvideo2_30s.mp4'

export default {
  name: 'App',
  components: {
    Banner,
    Cover,
    Content,
    HeadBar,
    Editor,
    GoodLife,
    Logo,
    FbComment,
    Foot,
    Indicator,
    ReadMore,
    Relate,
    Share,
    PhotoLink
  },
  data() {
    return{
      ImgBanner: ImgBanner,
      people_1: people_1,
      people_2: people_2,
      people_3: people_3,
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
      relate_3: relate_3,
      relate_4: relate_4,
      video: video,
      videoPC: video_pc
    }
  },
}
</script>

<style>
#app {
  font-size: 16px;
  line-height: 1.5;
  font-family: Arial, Microsoft JhengHei, sans-serif;
  word-wrap: break-word;
  text-align: justify;
  height: 100vh;
  width: 100%;
}
</style>

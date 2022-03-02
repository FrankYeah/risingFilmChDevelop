<template>
  <div class="about">
    <boxWidth>
      <headTop>
        <generalTitle :title="'關於風度'"></generalTitle>
      </headTop>
      <div class="about-pre about-desktop">風度影業凝聚資源挹注台灣影視人才，結合資源、創意、商業模式，<br>開創台灣影視新局。</div>
      <div class="about-pre about-rwd">風度影業凝聚資源挹注台灣影視人才，結合資源、創意、商業模式，開創台灣影視新局。</div>
    </boxWidth>
    <div class="about-post-box">
      <img class="about-post" :src="require('@/assets/img/about/post.jpg')" alt="post">
    </div>
    <boxWidth>
      <div class="about-post-head1">2022年風度影業開展佈局，與影視產業其他金獎團隊結盟合作</div>
      <div class="about-post-head2">由何蔚庭監製、鄺盛導演領軍，與好萊塢虛擬製作團隊聯合拍攝國際影片</div>
      <div class="about-desktop">
      <div class="about-post-text1">行銷部門整合市場與製作，以產業加值為目標，透過多元跨界、多媒體的溝通方式，<br>耕耘累積品牌價值，並依產業界各環節專業人士之職務屬性，推廣合適的虛擬製作觀念與思維</div>
      <div class="about-post-text2">美國虛擬攝影棚搭建專業顧問來台協力，共同打造 270度圓弧形的LED虛擬攝影棚，建構國際化影視製作流程</div>
      </div>
    </boxWidth>
    <div class="about-banner-box">
      <img class="about-banner" :src="require('@/assets/img/about/banner2.png')" alt="post">
    </div>

    <boxWidth class="about-rwd">
      <div class="about-post-text1">行銷部門整合市場與製作，以產業加值為目標，透過多元跨界、多媒體的溝通方式，耕耘累積品牌價值，並依產業界各環節專業人士之職務屬性，推廣合適的虛擬製作觀念與思維</div>
      <div class="about-post-text2">美國虛擬攝影棚搭建專業顧問來台協力，共同打造 270度圓弧形的LED虛擬攝影棚，建構國際化影視製作流程</div>
    </boxWidth>

    <boxWidth>
      <div class="about-member-box">
        <div>專業團隊</div>
        <div>集結業界開發/製作/行銷專家，打造一條龍產製商業模式</div>
      </div>
      <div class="about-intro">
        <div class="about-team-box" 
          v-for="(team, index) in teamList"
          :key="index"
          @click="selectPerson(index)"
        >
          <div class="about-person-box">
            <img class="about-person" v-lazy="team.person" alt="person">
          </div>  
          <div class="about-name">{{ team.name }}</div>
          <div class="about-name-title">{{ team.title }}</div>
        </div>
        
      </div>
      <div class="about-partner-title">合作夥伴</div>
      <div class="about-partner-box">
        <img class="about-partner"
          v-for="(partner, index) in partnerList"
          :key="index"
          v-lazy="partner.link" alt="person"
        >
      </div>
      <generalPopup :isShowPopup="isPersonPopup" @switchPopup="switchPopup">
        <div class="about-popup-row">
          <img class="about-popup-person" :src="selectedPerson.person2" alt="post">
          <div class="about-popup-column">
            <div class="about-popup-title">{{ selectedPerson.name }}</div>
            <div class="about-popup-sub">{{ selectedPerson.title }}</div>
            <div class="about-popup-desc" v-html="selectedPerson.desc"></div>
            <div v-if="selectedPerson.awards.length != 0" class="about-popup-awards">得獎</div>
            <div class="about-popup-award"
              v-for="(award, index) in selectedPerson.awards"
              :key="index">{{ award.name }}</div>
          </div>
        </div>
      </generalPopup>
    </boxWidth>
  </div>
</template>

<script>

import { teamList } from '@/assets/list/teamList'
import { partnerList } from '@/assets/list/partnerList'
export default {
  // head: {
  //   title: 'RISING FILMS',
  //   meta: [
  //     { name: 'keywords', content: 'RISING FILMS'},
  //   ]
  // },
  layout: 'default',
  components: {
    boxWidth: require('~/components/general-boxwidth.vue').default,
    headTop: require('~/components/general-headtop.vue').default,
    generalTitle: require('~/components/general-title.vue').default,
    generalPopup: require('~/components/general-popup.vue').default
  },
  props: {
    
  },
  data () {
    return {
      teamList: teamList,
      partnerList: partnerList,
      isPersonPopup: false,
      selectedPerson: {
        name: '',
        title: '',
        person2: require('@/assets/img/about/Eliza2.png'),
        desc: '',
        awards: []
      }
    }
  },
  computed: {

  },
  methods: {
    selectPerson(index) {
      this.isPersonPopup = true
      this.selectedPerson = teamList[index]
    },
    switchPopup (isPopup) {
      this.isPersonPopup = isPopup
    }
  },
  watch: {
    
  }
}
</script>

<style lang="scss" scoped>

.about {
  padding-bottom: 60px;

  &-desktop {
    display: block !important;
  }

  &-rwd {
    display: none !important;
  }

  &-pre {
    display: flex;
    align-items: center;
    text-align: justify;
    margin-top: 50px;
    font-size: 24px;
  }

  &-post-box {
    text-align: center;
  }

  &-post {
    max-width: 1000px;
    width: 100%;
    margin-top: 57px;
    padding: 0px 27px;
    text-align: center;
  }

  &-post-head1 {
    margin-top: 71px;
    font-size: 14px;
    opacity: 0.7;
  }

  &-post-head2 {
    margin-top: 12px;
    font-size: 14px;
    opacity: 0.7;
  }

  &-post-text1 {
    margin-top: 39px;
    font-size: 14px;
    text-align: justify;
    opacity: 0.7;
  }

  &-post-text2 {
    margin-top: 20px;
    font-size: 14px;
    text-align: justify;
    opacity: 0.7;
  }

  &-banner-box {
    text-align: center;
  }

  &-banner {
    max-width: 1000px;
    width: 100%;
    padding: 0px 27px;
    margin-top: 80px;
    text-align: center;
  }

  &-member-box {
    display: flex;
    align-items: center;
    margin-top: 112px;
    
    & div:first-child {
      margin-right: 48px;
      font-size: 24px;
    }
  }

  &-intro {
    width: 900px;
    margin: 0px auto 25px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  &-team-box {
    margin-top: 50px;
    text-align: center;
    cursor: pointer;

    &:hover {
      
      .about-person {
        transform: scale(1.1);
      }
    }
  }

  &-person-box {
    border-radius: 100%;
    overflow: hidden;
  }

  &-person {
    width: 260px;
    transition: all 0.4s;
    transition-timing-function: ease-in-out;
  }

  &-name {
    margin-top: 16px;
    font-size: 32px;
  }

  &-name-title {
    margin-top: 4px;
    opacity: 0.5;
  }

  &-partner-title {
    margin-top: 100px;
    font-size: 24px;
  }

  &-partner-box {
    width: 900px;
    margin: 20px auto 80px;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  &-partner {
    width: 195px;
    height: 100%;
  }

  &-popup {

    &-row {
      display: flex;
    }

    &-column {
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    &-person {
      width: 275px;
      margin-right: 36px;
    }

    &-title {
      font-size: 24px;
    }

    &-sub {
      margin-top: 10px;
      opacity: 0.5;
    }

    &-desc {
      margin: 23px 34px 0px 0px;
      font-size: 14px;
      text-align: justify;
      opacity: 0.5;
    }

    &-awards {
      margin: 32px 0px 12px;
    }

    &-award {
      margin-bottom: 8px;
      font-size: 14px;
      opacity: 0.5;
    }
  }
  
}

@media( max-width: 1023px ){

.about {
  padding-bottom: 0px;

  &-desktop {
    display: none !important;;
  }

  &-rwd {
    display: block !important;
  }

  &-pre {
    margin-top: 30px;
    font-size: 18px;
  }

  &-post-box {
    
  }

  &-post {
    margin-top: 42px;
    padding: 0px;
  }

  &-post-head1 {
    margin-top: 48px;
  }

  &-post-head2 {
    margin-top: 22px;
  }

  &-post-text1 {
    width: 100%;
  }

  &-post-text2 {
    margin-top: 30px;
  }

  &-banner-box {
    
  }

  &-banner {
    margin-top: 48px;
    padding: 0px;
  }

  &-member-box {
    flex-direction: column;
    align-items: flex-start;
    margin-top: 91px;
    
    & div:first-child {
      margin-right: 0px;
      font-size: 24px;
    }

    & div:last-child {
      margin-top: 16px;
    }
  }

  &-intro {
    width: 100%;
  }

  &-team-box {
    max-width: 180px;
    width: 50%;
    margin-top: 32px;
  }

  &-person {
    width: 90%;
  }

  &-name {
    font-size: 18px;
  }

  &-name-title {
    width: 130px;
    margin: 9px auto 0px;
  }

  &-partner-title {
    font-size: 24px;
    margin: 72px 0px 40px;
  }

  &-partner-box {
    width: 100%;
    margin: 20px auto 40px;
  }

  &-partner {
    max-width: 180px;
    width: 45%;
    height: 100%;
  }

  &-popup {

    &-row {
      flex-direction: column;
      align-items: center;
    }

    &-column {
      display: block;
    }

    &-person {
      width: 157px;
      align-items: center;
      margin-right: 0px;
    }

    &-title {
      margin-top: 18px;
      text-align: center;
    }

    &-sub {
      margin-top: 8px;
      text-align: center;
      font-size: 18px;
    }

    &-desc {
      
      margin: 13px 0px 0px 0px;
    }

    &-awards {
      font-size: 18px;
      margin: 24px 0px 18px;
    }

    &-award {
      
    }
  }
  
}

}


</style>
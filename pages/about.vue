<template>
  <div class="about">
    <boxWidth>
      <headTop>
        <generalTitle :title="'About'"></generalTitle>
      </headTop>
      <div class="about-pre">
        <div>風度影業<span class="about-pre-en">RISING FILM</span> </div>
        <div>風度影業凝聚資源挹注台灣影視 人才，結合資源、創意、商業模 式， 開創台灣影視新局。</div>
      </div>

    </boxWidth>
    <div class="about-post-box">
      <img class="about-post" :src="require('@/assets/img/about/post.jpg')" alt="post">
    </div>
    <boxWidth>
      <div class="about-desc">2021年投資製作何蔚庭導演《青春弒戀》，<br>獲得金馬獎入圍五項大獎。</div>
      <div class="about-member-box">
        <div>團隊成員</div>
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
          <div>
            <div class="about-popup-title">{{ selectedPerson.name }}</div>
            <div class="about-popup-sub">{{ selectedPerson.title }}</div>
            <div class="about-popup-desc">{{ selectedPerson.desc }}</div>
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
  head: {
    title: 'RISING FILMS',
    meta: [
      { name: 'keywords', content: 'RISING FILMS'},
    ]
  },
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

  &-pre {
    display: flex;
    align-items: center;
    margin-top: 32px;

    &-en {
      margin-left: 16px;
    }

    & div:first-child {
      width: 50%;
      font-size: 36px;
    }

    & div:last-child {
      width: 50%;
      line-height: 1.5;
    }
  }

  &-post-box {
    text-align: center;
  }

  &-post {
    max-width: 1000px;
    width: 100%;
    margin-top: 64px;
    text-align: center;
  }

  &-desc {
    width: 650px;
    margin: 41px auto 0px;
    text-align: center;
    line-height: 1.5;
  }

  &-member-box {
    display: flex;
    align-items: flex-end;
    margin-top: 112px;
    
    & div:first-child {
      margin-right: 48px;
      font-size: 32px;
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
        transform: scale(1.2);
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
    margin-top: 12px;
    font-size: 32px;
  }

  &-name-title {
    margin-top: 6px;
    opacity: 0.5;
  }

  &-partner-title {
    margin-top: 100px;
    font-size: 32px;
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
  }

  &-popup {

    &-row {
      display: flex;
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
      margin-top: 23px;
      line-height: 1.5;
      font-size: 14px;
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


  &-pre {
    flex-direction: column;
    margin-top: 22px;width: 100%;

    &-en {
      margin-left: 12px;
      font-size: 22px;
    }

    & div:first-child {
      display: flex;
      align-items: center;
      width: 100%;
      font-size: 24px;
    }

    & div:last-child {
      width: 100%;
      margin-top: 22px;
    }
  }

  &-post-box {
    
  }

  &-post {
    margin-top: 36px;
  }

  &-desc {
    width: 100%;
    margin-top: 31px;
  }

  &-member-box {
    flex-direction: column;
    align-items: flex-start;
    margin-top: 78px;
    
    & div:first-child {
      margin-right: 0px;
      font-size: 24px;
    }

    & div:last-child {
      margin-top: 16px;
      line-height: 1.3;
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
  }

  &-popup {

    &-row {
      flex-direction: column;
      align-items: center;
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
      margin-top: 13px;
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
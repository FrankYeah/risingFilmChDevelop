<template>
  <div class="top">
    
    <nuxt-link class="top-logo" to="/">
      <img
        :src="require('@/assets/img/icon/logo.png')"
        alt="logo"
      >
    </nuxt-link>
    <img @click="isShowMenu = true"
      class="top-menu top-rwd"
      :src="require('@/assets/img/icon/menu.png')"
      alt="menu"
    >

    <div class="top-header-href-box top-desktop">
      <nuxt-link to="/about" class="top-header-link">
        <div @click="closeMenu"
          @mouseover="hoverLink('about')" 
          @mouseleave="leaveLink"
          :class="[`top-header-href top-header-href1 top-popup-animate1`,
          {'top-popup-href-dark': !isHover.about},
          {'top-popup-href-light': isAllLight}]"
        >關於</div>
        <div @click="closeMenu" :class="['top-header-line', {'top-popup-line-show top-header-line1': isHover.about}]"></div>
      </nuxt-link>

      <nuxt-link to="/works" class="top-header-link">
        <div
          @mouseover="hoverLink('development')" 
          @mouseleave="leaveLink"
          :class="['top-header-href top-header-href2 top-popup-animate2', {'top-popup-href-dark': !isHover.development}, {'top-popup-href-light': isAllLight}]"
        >作品</div>
        <div @click="closeMenu" @mouseover="hoverLink('development')" :class="['top-header-line', {'top-popup-line-show top-header-line2': isHover.development}]" ></div>
      </nuxt-link>

      <!-- <div v-if="isHover.developmentIn"
        @mouseover="hoverLink('development')"
        class="top-header-href-s-box"
      >
        <nuxt-link to="/works#other">
          <div @click="closeMenu"
            @mouseover="hoverLink('development')"
            class="top-header-href-s"
          >參與</div>
        </nuxt-link>
        <nuxt-link to="/works#production">
          <div @click="closeMenu"
            @mouseover="hoverLink('development')"
            class="top-header-href-s"
          >製作</div>
        </nuxt-link>
        <nuxt-link to="/works#development">
          <div @click="closeMenu"
            @mouseover="hoverLink('development')"
            class="top-header-href-s top-header-href-s-last"
          >開發</div>
        </nuxt-link>
      </div> -->
      <nuxt-link to="/virtual" class="top-header-link">
        <div @click="closeMenu"
          @mouseover="hoverLink('virtual')" 
          @mouseleave="leaveLink" 
          :class="['top-header-href top-header-href4 top-popup-animate3', {'top-popup-href-dark': !isHover.virtual}, {'top-popup-href-light': isAllLight}]"
        >虛擬製作</div>
        <div @click="closeMenu" :class="['top-header-line', {'top-popup-line-show top-header-line4': isHover.virtual}]"></div>
      </nuxt-link>
      <nuxt-link to="/contact" class="top-header-link">
        <div @click="closeMenu"
          @mouseover="hoverLink('contact')" 
          @mouseleave="leaveLink" 
          :class="['top-header-href top-header-href5 top-popup-animate4', {'top-popup-href-dark': !isHover.contact}, {'top-popup-href-light': isAllLight}]"
        >專人洽詢</div>
        <div @click="closeMenu" :class="['top-header-line', {'top-popup-line-show top-header-line5': isHover.contact}]"></div>
      </nuxt-link>
      <div class="top-header-language top-popup-animate5">
        <span>中</span>
        ｜
        <a href="https://frankyeah.github.io/risingFilmEn/" target="_blank" class="top-header-lang" style="opacity: 0.3; font-family: 'Roboto';">EN</a>
      </div>
    </div>
    

    <!-- popup -->
    <transition name="fade">
      <div v-if="isShowMenu"
      :class="[`top-popup`]"
      >
        <div class="top-popup-language top-popup-animate5">
          <span>中</span>
          ｜
          <a href="https://frankyeah.github.io/risingFilmEn/" target="_blank" class="top-popup-lang" style="opacity: 0.3; font-family: 'Roboto';">EN</a>
        </div>
        <div class="top-popup-row">
          <div></div>
          <img @click="closeMenu"
            class="top-popup-animate6"
            :src="require('@/assets/img/icon/close.png')"
            alt="close"
          >
        </div>
        <div class="top-popup-link">
          <nuxt-link to="/about">
            <div @click="closeMenu"
              @mouseover="hoverLink('about')" 
              @mouseleave="leaveLink"
              :class="[`top-popup-href top-popup-href1 top-popup-animate1`,
              {'top-popup-href-dark': !isHover.about},
              {'top-popup-href-light': isAllLight}]"
            >關於</div>
            <div @click="closeMenu" :class="['top-popup-line', {'top-popup-line-show top-popup-line1': isHover.about}]"></div>
          </nuxt-link>

          <div @click="isHover.developmentIn = true"
            @mouseover="hoverLink('development')"
            :class="['top-popup-href top-popup-href2 top-popup-animate2', {'top-popup-href-dark': !isHover.development}, {'top-popup-href-light': isAllLight}]"
          >作品</div>
          <div @click="closeMenu" @mouseover="hoverLink('development')" :class="['top-popup-line', {'top-popup-line-show top-popup-line2': isHover.development}]" ></div>

          <div v-if="isHover.developmentIn"
            @mouseover="hoverLink('development')"
            class="top-popup-href-s-box"
          >
            <nuxt-link to="/works#development">
              <div @click="closeMenu"
                @mouseover="hoverLink('development')"
                class="top-popup-href-s"
              >開發</div>
            </nuxt-link>
            <nuxt-link to="/works#production">
              <div @click="closeMenu"
                @mouseover="hoverLink('development')"
                class="top-popup-href-s"
              >製作</div>
            </nuxt-link>
            <nuxt-link to="/works#other">
              <div @click="closeMenu"
                @mouseover="hoverLink('development')"
                class="top-popup-href-s top-popup-href-s-last"
              >參與</div>
            </nuxt-link>
          </div>
          <nuxt-link to="/virtual">
            <div @click="closeMenu"
              @mouseover="hoverLink('virtual')" 
              @mouseleave="leaveLink" 
              :class="['top-popup-href top-popup-href4 top-popup-animate3', {'top-popup-href-dark': !isHover.virtual}, {'top-popup-href-light': isAllLight}]"
            >虛擬製作</div>
            <div @click="closeMenu" :class="['top-popup-line', {'top-popup-line-show top-popup-line4': isHover.virtual}]"></div>
          </nuxt-link>
          <nuxt-link to="/contact">
            <div @click="closeMenu"
              @mouseover="hoverLink('contact')" 
              @mouseleave="leaveLink" 
              :class="['top-popup-href top-popup-href5 top-popup-animate4', {'top-popup-href-dark': !isHover.contact}, {'top-popup-href-light': isAllLight}]"
            >專人洽詢</div>
            <div @click="closeMenu" :class="['top-popup-line', {'top-popup-line-show top-popup-line5': isHover.contact}]"></div>
          </nuxt-link>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  components: {

  },
  props: {
    
  },
  data () {
    return {
      isShowMenu: false,
      isAllLight: true,
      isHover: {
        about: false,
        development: false,
        developmentIn: false,
        virtual: false,
        contact: false ,
      }
    }
  },
  computed: {

  },
  methods: {
    goHomePage() {
      this.$router.push('/')
    },
    hoverLink(link) {
      switch (link) {
          case 'about':
            this.isHover.about = true
            this.isHover.developmentIn = false
            this.isHover.development = false
            break;
          case 'development':
            this.isHover.development = true
            this.isHover.developmentIn = true
            break;
          case 'virtual':
            this.isHover.virtual = true
            this.isHover.developmentIn = false
            this.isHover.development = false
            break;
          case 'contact':
            this.isHover.contact = true
            this.isHover.developmentIn = false
            this.isHover.development = false
            break;
          default:
        }
    },
    leaveLink() {
      this.isHover.about = false
      this.isHover.development = false
      this.isHover.developmentIn = false
      this.isHover.virtual = false
      this.isHover.contact = false
    },
    closeMenu() {
      this.isShowMenu = false
      this.leaveLink()
    }
  },
  watch: {
    isHover: {
      handler: function() {
        this.isAllLight = false
        setTimeout(()=> {
          if(!this.isHover.about && !this.isHover.development && !this.isHover.developmentIn && !this.isHover.virtual && !this.isHover.contact) {
            this.isAllLight = true
          }
        }, 500)
      },
      deep: true,
      immediate: true
    },
  }
}
</script>

<style lang="scss">

.top {
  position: fixed;
  top: 0px;
  left: 0px;
  width: calc(100% - 64px);
  z-index: 3;

  &-desktop {
    display: block;
  }

  &-rwd {
    display: none;
  }

  &-logo {
    position: fixed;
    top: 32px;
    left: 32px;

    & img {
      width: 42px;
      height: 100%;
      transition: all 0.4s;
      transition-timing-function: ease-in-out;
      cursor: pointer;

      &:hover {
      }
    }

  }

  &-menu {
    position: fixed;
    top: 32px;
    right: 32px;
    width: 52px;
    height: 52px;
    opacity: 0.5;
    transition: all 0.4s;
    transition-timing-function: ease-in-out;
    cursor: pointer;

    &:hover {
      opacity: 1;
    }
  }

  &-header {

    &-href-box {
      position: fixed;
      top: 32px;
      right: 32px;
      display: flex;
      align-items: center;
    }

    &-href {
      margin: 20px 0px 0px 30px;
      padding: 0px 0px 8px;
      transition: all 0.4s;
      transition-timing-function: ease-in-out;
      cursor: pointer;

      :hover {
        color: white;
      }
    }

    &-link {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
    }

    &-href1 {
      width: 40px;
    }

    &-href2 {
      position: relative;
      width: 40px;
    }

    &-href4 {
      width: 80px;
    }

    &-href5 {
      width: 80px;
    }

    &-line {
      width: 1px;
      height: 1.5px;
      transform: translateX(-2px);
      background-color: transparent;
      transition: 0.3s;
    }

    &-line1 {
      width: 36px !important;
    }

    &-line2 {
      width: 36px !important;
    }

    &-line4 {
      width: 74px !important;
    }

    &-line5 {
      width: 74px !important;
    }

    &-href-s-box {
      position: absolute;
      top: 40px;
      left: 34px;
      display: flex;
      padding: 17px 0px 0px 0px;

      & a:first-child {
        margin-top: 0px;
      }
    }

    &-href-s {
      padding-right: 30px;
      transition: all 0.4s;
      transition-timing-function: ease-in-out;
      opacity: 0.15; 

      &:hover {
        opacity: 1;
      }
    }

    &-language {
      margin: 20px 0px 0px 50px;
      padding: 0px 0px 8px;
    }

    &-lang {
      transition: all 0.4s;
      transition-timing-function: ease-in-out;
      cursor: pointer;

      &:hover {
        opacity: 1 !important;
      }
    }
  }

  &-row {
    display: flex;
    justify-content: space-between;

    & img {
      cursor: pointer;
    }
    
    & img:first-child {
      width: 42px;
      height: 100%;
    }

    & img:last-child {
      width: 52px;
      height: 100%;
    }
  }

  &-popup {
    position: fixed;
    right: 0px;
    top: 0px;
    width: calc(100% - 64px);
    height: 100vh;
    padding: 32px 32px 0px 32px;
    background-color: #29292A;

    &-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 24px;

      & img {
        width: 30px;
        opacity: 0.5;
        transition: all 0.4s;
        transition-timing-function: ease-in-out;
        cursor: pointer;

        &:hover {
          opacity: 1;
        }
      }
    }

    &-language {
      position: fixed;
      bottom: 32px;
      right: 32px;
    }

    &-lang {
      transition: all 0.4s;
      transition-timing-function: ease-in-out;
      cursor: pointer;

      &:hover {
        opacity: 1 !important;
      }
    }

    &-link {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      font-size: 24px;

      & a:first-child {
        margin-top: 20px;
      }
    }

    &-href {
      margin-top: 60px;
      padding: 0px 0px 8px;
      transition: all 0.4s;
      transition-timing-function: ease-in-out;
      cursor: pointer;

      :hover {
        color: white;
      }
    }

    &-href-light {
      opacity: 1 !important;
    }

    &-href-dark {
      opacity: 0.2;
    }

    &-href1 {
      width: 54px;
    }

    &-href2 {
      width: 54px;
    }

    &-href4 {
      width: 108px;
    }

    &-href5 {
      width: 108px;
    }

    &-animate1 {
      animation: hrefAnimate; /* referring directly to the animation's @keyframe declaration */
      animation-duration: 1s;
      animation-delay: 0.5s;
      animation-fill-mode: backwards;
      animation-timing-function: cubic-bezier(.94,-0.01,.08,1);
    }

    &-animate2 {
      animation: hrefAnimate; /* referring directly to the animation's @keyframe declaration */
      animation-duration: 1s;
      animation-delay: 0.6s;
      animation-fill-mode: backwards;
      animation-timing-function: cubic-bezier(.94,-0.01,.08,1);
    }

    &-animate3 {
      animation: hrefAnimate; /* referring directly to the animation's @keyframe declaration */
      animation-duration: 1s;
      animation-delay: 0.7s;
      animation-fill-mode: backwards;
      animation-timing-function: cubic-bezier(.94,-0.01,.08,1);
    }

    &-animate4 {
      animation: hrefAnimate; /* referring directly to the animation's @keyframe declaration */
      animation-duration: 1s;
      animation-delay: 0.8s;
      animation-fill-mode: backwards;
      animation-timing-function: cubic-bezier(.94,-0.01,.08,1);
    }

    &-animate5 {
      animation: hrefAnimate; /* referring directly to the animation's @keyframe declaration */
      animation-duration: 1s;
      animation-delay: 1.1s;
      animation-fill-mode: backwards;
      animation-timing-function: cubic-bezier(.94,-0.01,.08,1);
    }

    &-animate6 {
      animation: closeAnimate; /* referring directly to the animation's @keyframe declaration */
      animation-duration: 1s;
      animation-delay: 1.1s;
      animation-fill-mode: backwards;
      animation-timing-function: cubic-bezier(.94,-0.01,.08,1);
    }

    &-line {
      width: 1px;
      height: 1.5px;
      background-color: transparent;
      transition: 0.3s;
    }

    &-line-show {
      background-color: white;
    }

    &-line-hide {
      background-color: transparent;
    }

    &-line1 {
      width: 48px;
    }

    &-line2 {
      width: 48px;
    }

    &-line4 {
      width: 96px;
    }

    &-line5 {
      width: 96px;
    }

    &-href-s-box {
      display: flex;
      padding: 17px 0px 0px 0px;
      font-size: 24px;

      & a:first-child {
        margin-top: 0px;
      }
    }

    &-href-s {
      padding-right: 48px;
      transition: all 0.4s;
      transition-timing-function: ease-in-out;
      opacity: 0.15; 

      &:hover {
        opacity: 1;
      }
    }

    &-href-s-last {
      padding-right: 0px;
    }
  }
  
}

// 動態

// bg 動態
.fade-enter-active {
  transition: width .6s;
  transition-timing-function: cubic-bezier(.94,-0.01,.08,1);
}

.fade-enter {
  width: 0px;
}

.fade-leave {
  width: 0px;
}

@keyframes hrefAnimate {
  0%   { opacity: 0; transform: translateX(60px); }
  30%  { opacity: 0; }
  66%  {  }
  99%  { opacity: 1; transform: translateX(0px); }
}

@keyframes closeAnimate {
  0%   { opacity: 0; transform: translateX(60px); }
  30%  { opacity: 0; }
  66%  {  }
  99%  { opacity: 0.5; transform: translateX(0px); }
}


@media( max-width: 1023px ){

.top {

  &-desktop {
    display: none;
  }

  &-rwd {
    display: block;
  }
  

  &-logo {
    top: 29px;
    left: 20px;

    & img {
    }

  }

  &-menu {
    top: 29px;
    right: 20px;
  }

  &-row {
    

    & img {
      
    }
    
    & img:first-child {
      
    }

    & img:last-child {
      
    }
  }

  &-popup {
    

    &-row {
      

      & img {
        
      }
    }

    &-lang {

    }

    &-link {

      & a:first-child {
        
      }
    }

    &-href {
      
    }

    &-href-light {
      
    }

    &-href-dark {
      opacity: 1;
    }

    &-href1 {
      
    }

    &-href2 {
      
    }

    &-href4 {
      
    }

    &-href5 {
      
    }

    &-line {
      
    }

    &-line-show {
      // background-color: transparent;
    }

    &-line-hide {
      
    }

    &-line1 {
      
    }

    &-line2 {
      
    }

    &-line4 {
      
    }

    &-line5 {
      
    }

    &-href-s-box {

      & a:first-child {
        
      }
    }

    &-href-s {
      opacity: 1; 
    }

    &-href-s-last {

    }
  }
  
}

}


</style>
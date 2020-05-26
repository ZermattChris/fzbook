<template>
  <ion-app>
    <ion-page>

      <ion-header class="ion-no-border">
        <ion-toolbar color="white">
          <ion-title class="ion-text-center">
            <div class="ion-hide-md-down logo-spacer"></div>
            <img height="100em" alt="FLYZermatt Logo" src="./assets/fzlogo-forlight.svg" />
            
            <div class="ion-hide-md-down logo-spacer"></div>
          </ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-content ref="content" scrollEvents="true" onIonScroll="">
        <ion-grid class="ion-no-padding">
          <ion-row>
            <ion-col size="2" class="maroon ion-hide-md-down"></ion-col>
            <ion-col size-md="8" size="12">

            <!-- This is the Booking form in a slider -->
            <Booking ref="booking" @changed="onChangedSlide"></Booking>

            </ion-col>
            <ion-col size="2" class="maroon ion-hide-md-down"></ion-col>
          </ion-row>
        </ion-grid>
      </ion-content>


      <ion-footer class="ion-no-border">
        <ion-toolbar>
          <div id="leftBtnSpacer" class="footer-spacer ion-float-left ion-hide-sm-down"></div>
          <ion-buttons class="ion-float-left">
            <ion-button :disabled="firstSlide" @click="onBackBtn"> 
              Back
            </ion-button>
          </ion-buttons>
          <div id="rightBtnSpacer" class="footer-spacer ion-float-right ion-hide-sm-down"></div>
          <ion-buttons class="ion-float-right">
            <ion-button :disabled="lastSlide" fill="solid" color="primary" @click="onContinueBtn">
              Continue
            </ion-button>
          </ion-buttons>
        </ion-toolbar>
      </ion-footer>

      <ion-fab vertical="bottom" horizontal="center" slot="fixed">
        <ion-fab-button class="tweak-to-top-btn" title="Scroll to Top..." size="small" @click="scrollToTop"> 
          <ion-icon name="arrow-up"></ion-icon>
        </ion-fab-button>
      </ion-fab>

    </ion-page>

  </ion-app>
</template>

<script>
  //import Vue from 'vue'
  //import Bus from './Bus';

  import Booking from "./components/Booking"

  import { attach, arrowUp } from "ionicons/icons";
  import { addIcons } from "ionicons";


  addIcons({
    "ios-attach": attach.ios,
    "md-attach": attach.md,
    "ios-arrow-up": arrowUp.ios,
    "md-arrow-up": arrowUp.md
  });

  export default {
    name: "App",
    components: {
      Booking
    },
    data: function () {
      return {
          firstSlide: true,
          lastSlide: false
      }
    },
    computed: {
      // numberOfSlides: function () {
      //   return this.$refs.booking.slides().length
      // }
    },
    methods: {
      scrollToTop () { this.$refs.content.scrollToTop(200) },
      onContinueBtn () { this.$refs.booking.nextSlide() },
      onBackBtn () { this.$refs.booking.prevSlide() },
      
      onChangedSlide ($e) {
        if ($e.target.swiper.isBeginning) {
          this.firstSlide = true
        } else {
          this.firstSlide = false
        }
        if ($e.target.swiper.isEnd > 0) {
          this.lastSlide = true
        } else {
          this.lastSlide = false
        }
      }
    }
  };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.footer-spacer {
    height: 5px;
    width: 16vw;
    display: inline-block;
    /* background-color: yellow; */
}

.tweak-to-top-btn {
    position: relative;
    top: -15px;
}

.logo-spacer {
    height: 2em;
    width: 100%;
}

.ion-no-border:after,
.ion-no-border:before  {
  background-image: none !important;
}



</style>

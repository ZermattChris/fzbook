<template>

  <div id="main-contents" class="big-vertical-box">
    <!-- <IonButton onClick={()=>prevSlide()}>Prev</IonButton>
    <IonButton onClick={()=>nextSlide()}>Next</IonButton> -->
    <ion-slides ref="swiper" @ionSlideDidChange="$emit('changed', $event)" >
      <ion-slide>
        <div>
          <h2><ion-icon class="step-icon rotate-45" icon="airplane"></ion-icon>1. Get Started...</h2>
          <div class="form-container">
            <ul>
              <li>Page Label + Short note explaining why we collect this info</li>
              <li>Number of People (integer between 1 and X).</li>
              <li>Flight Date (Date – Specific Day)</li>
              <li>Flight Type (Scenic, Classic, Elite)</li>
              <li>Including Photos/Videos? </li>
            </ul>
          </div>
        </div>
      </ion-slide>

      <ion-slide>
        <div>
          <h2><ion-icon class="step-icon" icon="airplane" ></ion-icon>2. Choose your flight Time...</h2>
          <div class="form-container">
            <ul>
              <li>Page Label + Details selected from Step 1</li>
              <li>Choose Flight Time Slot (a la EasyJet). Use the selected Day from Step 1 and 
                bracket is with either 2 or 3 days on either side, showing current availability</li>
            </ul>
          </div>
        </div>
      </ion-slide>

      <ion-slide>
        <div>
          <h2><ion-icon class="step-icon" icon="airplane"></ion-icon>3. Your Group...</h2>
          <div class="form-container">
            <ul>
              <li>Contact Person</li>
                <ul>
                  <li>First Name</li>
                  <li>Last Name</li>
                  <li>Male/Female</li>
                  <li>Email</li>
                  <li>Phone</li>
                  <li>Arrival Day + Time (optional)</li>
                  <li>Departure Day + Time (optional)</li>
                  <li>Age</li>
                  <li>Weight</li>
                  <li>Fitness Level</li>
                </ul>
              <li>2 to x for multi person bookings here... (only enable when Contact Person filled in properly</li>
                <ul>
                  <li>Name</li>
                  <li>Male/Female</li>
                  <li>Age</li>
                  <li>Weight</li>
                  <li>Fitness Level</li>
                </ul>
            </ul>
          </div>
          <div class="temp-spacer-box"></div>
          <p>Just some more stuff to make the container scroll.</p>
        </div>
      </ion-slide>

      <ion-slide>
        <div>
          <h2><ion-icon class="step-icon" icon="airplane"></ion-icon>4. Optional Note to us</h2>
          <div class="form-container">
            <ul>
              <li>Optional Note (we can give some simple examples for them, such as My 65 year old 
                mother wants to fly, but is nervous – or my husband is heavy, but very tall and super sporty)</li>
            </ul>
          </div>
        </div>
      </ion-slide>

      <ion-slide>
        <div>
          <h2><ion-icon class="step-icon" icon="airplane"></ion-icon>5. Review your Booking</h2>
          <div class="form-container">
            <ul>
              <li>Confirmation of input data (please check that email and phone number are correct!)</li>
              <li>Use the BACK button to make any corrections needed before continuing...</li>
            </ul>
          </div>
        </div>
      </ion-slide>

      <ion-slide>
        <div>
        <h2><ion-icon class="step-icon" icon="airplane"></ion-icon>6. Basic Tips and T&amp;Cs</h2>
          <div class="form-container">
            <ul>
              <li>What comes next after you book &amp; General Info (with link to detailed T&amp;Cs)</li>
            </ul>
          </div>
        </div>
      </ion-slide>

      <ion-slide>
        <div>
        <h2><ion-icon class="step-icon" icon="airplane"></ion-icon>7. Payment</h2>
          <div class="form-container">
            <ul>
              <li>At moment skip online payemts</li>
              <li>We can build this module, but leave it flagged=false</li>
              <li>Put the booking into the New Bookings Queue (and backup with current Email system?)</li>
            </ul>
          </div>
        </div>
      </ion-slide>

      <ion-slide>
        <div>
          <h2>Thanks for Booking with FlyZermatt!</h2>
          <p>We're looking forward to flying with you here in the mighty Zermatt Alps.</p>
          <div class="form-container">
            <ul>
              <li>Check your Email Inbox (and Spam/Junk folders) for confirmation email.</li>
              <li>Mail didn’t show up? Check your Email address and resend</li>
            </ul>
          </div>
          <ion-button fill="clear">FlyZermatt Home Page<ion-icon slot="start" icon={arrowBackSharp} ></ion-icon></ion-button>
        </div>
      </ion-slide>

    </ion-slides>
  </div>

</template>

<!-- Class Export -->
<script>

export default {
  name: 'Booking',
  props: {
    
  },
  methods: {
    test () {
      console.log("isEnd")
    },
    nextSlide () {
      const mySwiper = this.$refs.swiper
      //console.log(mySwiper.isEnd())
      mySwiper.slideNext()
    },
    prevSlide () {
      const mySwiper = this.$refs.swiper
      mySwiper.slidePrev()
    }
  }
}

</script>

<!-- Private CSS -->
<style scoped>

.container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

.container strong {
  font-size: 20px;
  line-height: 26px;
}

.container p {
  font-size: 16px;
  line-height: 22px;
  color: #8c8c8c;
  margin: 0;
}

.container a {
  text-decoration: none;
}


.big-vertical-box {
  display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	justify-content: flex-start;
  align-items: stretch;
  
  /* min-height: 1200px;; */
  /* background-color: rgb(255, 174, 53); */
  margin: 0 !important;
  padding: 0 !important;
}

/* This f**ker was causing the Slide contents to be 'vertically' centered! Arrrgh! */
.swiper-zoom-container {
  align-items: start;
}

ion-slides {
  padding-top: 20px !important;
  /* height: 100%; */
}

.step-icon {
  margin-right: 10px;
  font-size: 32px;
  color: rgb(236, 0, 185);
}
.rotate-45 {
  transform: rotate(-45deg);
}
.form-container {
  text-align: left;
}

.temp-spacer-box {
  height: 500px;
  background-color: rgb(236, 167, 135);
}
</style>

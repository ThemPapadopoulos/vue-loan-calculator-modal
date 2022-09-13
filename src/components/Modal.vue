
<script>
import Slider from '@vueform/slider'
import Header from './Header.vue'
import Footer from './Footer.vue'

export default {
  components: {
    Slider,
    Header,
    Footer,

  },
  data() {
    return {

      showModal: false,
      upfront: 10000,
      duration: 24,
      price: 20000,

    }

  },

  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
  formatNumber(num) {
    let parsed = Math.round(num) 
    
    
    return parsed.toLocaleString('de-DE');
    }
  },
  computed: {
    
  }
}

</script>

<template>
  <div>
    <div v-if="showModal" class="modal">
      <button class="modal-close" @click="showModal = false">X</button>

      <Header />

      <div id="firstLabel">
        <p>Προκαταβολή</p>
        <span >{{ upfront.toLocaleString('de-DE') }}€</span>
      </div>

      <Slider
        class="slider-blue"
        id="downPayment"
        description="Lorem ipsum dolor sit amet, consectetur adipiscing elit"
        show-tooltip="drag"
        :format="{ suffix: ' €', thousand: '.' }"
        :max="price"
        :step="100"
        size="lg"
        v-model="upfront"
      />

      <div id="firstUnderLabel">
        <span>0€</span>
        <span>{{ price.toLocaleString('de-DE') }}€</span>
      </div>

      <div id="secondLabel">
        <p id="first">Διάρκεια</p>
        <span>{{ duration }}</span>
        <p id="monthsWord">μήνες</p>
      </div>

      <Slider
        id="duration"
        ticks="always"
        tick-size="4"
        :min="3"
        :max="72"
        class="slider-blue"
        show-tooltip="drag"
        size="lg"
        rules="integer|required"
        :messages="{ required: 'Επιλέξτε τον αριθμό των δόσεων' }"
        v-model="duration"
      />

      <div id="secondUnderLabel">
        <span>3 μήνες</span>
        <span>72 μήνες</span>
      </div>

      <p id="installment">
        Μηνιαία Δόση:
        <span>{{ formatNumber((price - upfront) / duration) }}€</span>
      </p>

      <Footer />

    </div>

    <div id="modalToggler" @click="toggleModal">Click Anywhere to Toggle Modal</div>
  </div>
</template>




<style src="@vueform/slider/themes/default.css">
</style>

<style  
 scoped>
p {
  margin: 0;
}
#modalToggler {
  z-index: -1;
  position: absolute;
 
  width: 100vw;
  height: 100vh;
  font-size: 24px;
  font-weight: 700;
}
.modal {
  background: #ffffff 0% 0% no-repeat padding-box;
  box-shadow: 0px 0px 40px #00000080;
  border-radius: 5px;
  opacity: 1;
  width: 655px;
  height: 508px;
  margin: 0 auto;
  display: table;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  -webkit-transform: translateY(-50%);
  -moz-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  -o-transform: translateY(-50%);
  transform: translateY(-50%);
  
}
.modal-close {
 cursor: pointer;
  position: absolute;
  color: #b7c8d0;
  background-color: white;
  border: none;
  top: 30px;
  right: 30px;

  width: 10px;
  height: 10px;
  /* UI Properties */
  opacity: 1;
}

.slider-blue {
  --slider-connect-bg: #01aed8;
  --slider-tooltip-bg: #01aed8;
  --slider-handle-ring-color: #3b82f630;
  --slider-handle-width: 26px;
  --slider-handle-height: 26px;
  --slider-handle-shadow: 0px 0px 10px #00000033;
}

#firstLabel {
  position: absolute;
  top: 135px;
  width: 100%;
  height: fit-content;
}

#secondLabel {
  position: absolute;
  top: 245px;
  width: 100%;
  height: fit-content;
}

#firstLabel p {
  /* Layout Properties */
  position: absolute;
  font-size: 15px;
  font-weight: 700;
  left: 112px;
  width: 95px;
  height: 20px;
  /* UI Properties */
  text-align: left;
  letter-spacing: 0px;
  color: #323232;
  opacity: 1;
}
#firstLabel span {
  position: absolute;
  font-size: 24px;
  font-weight: 700;
  left: 469px;
      top: -5px;
  width: 74px;
  height: 32px;
  text-align: right;
  letter-spacing: 0px;
  color: #323232;
  opacity: 1;
}

#firstUnderLabel {
  top: 205px;
  position: absolute;
  display: flex;
  justify-content: space-between;
  left: 112px;

  width: 432px;
  

  font-size: 14px;
  font-weight: 400;

  height: fit-content;
  text-align: center;
  letter-spacing: 0px;
  color: #b7c8d0;
  opacity: 1;
}

#first {
  position: absolute;
  font-size: 15px;
  font-weight: 700;
  left: 112px;
  width: 64px;
  top: 5px;

  height: 20px;
  text-align: left;
  letter-spacing: 0px;
  color: #323232;
  opacity: 1;
}
#secondLabel span {
  position: absolute;
  font-size: 24px;
  font-weight: 700;
  bottom: -30px;
  left: 421px;
  width: 74px;
  height: 32px;
  text-align: right;
  letter-spacing: 0px;
  color: #323232;
  opacity: 1;
}

#monthsWord {
  position: absolute;

  left: 500px;
}

#secondUnderLabel {
  position: absolute;
  display: flex;
  justify-content: space-between;
  left: 112px;
  top: 315px;
  width: 432px;
  height: fit-content;
  letter-spacing: 0px;
  color: #b7c8d0;
  opacity: 1;
  font-size: 14px;
  font-weight: 400;
}

#downPayment {
  position: absolute;
  top: 184px;
  left: 112px;
  width: 432px;
  height: 8px;
  background: #d8d8d8 0% 0% no-repeat padding-box;
  border-radius: 9px;
  opacity: 1;
}

#duration {
  position: absolute;
  top: 294px;
  left: 112px;
  width: 432px;
  height: 8px;
  background: #d8d8d8 0% 0% no-repeat padding-box;
  border-radius: 9px;
  opacity: 1;
}

#installment {
  position: absolute;
  top: 354px;

  width: 100%;
  height: 20px;
  text-align: center;
  letter-spacing: 0px;
  color: #323232;
  opacity: 1;
  font-size: 15px;
  font-weight: 700;
}
#installment span {
  font-size: 24px;
  font-weight: 700;
}

@media screen and (max-width: 600px) {

  .modal {
    overflow: hidden; 
    height: 100vh;
    width: 100vw;
    box-shadow: none;
  
  }
  #firstLabel p, #firstLabel span, #secondLabel,#firstUnderLabel,#secondUnderLabel, #installment {
    text-align: left;
  width: 85%;
margin-top: 10vh;
 left: 15px;
    font-size: 110% ;

   
  }
    #monthsWord {
      top: 5px;
left: 323px;
font-size: 90%;
  }
  #firstLabel p,#firstUnderLabel,#secondUnderLabel {
    left: 15px;
    width: 94%;
  }
  #firstLabel span
  {
    position: absolute;
    left: 300px;
  }

  #secondLabel span{
    left: 245px;
  }


#downPayment, #duration{
   margin-top: 10vh;
   margin-left: 15px;
   width: 90%;
   left: 0vw;
}

#first {
  left: 15px;
}
#installment{
  padding-top: 10vh;;
}
}

</style>

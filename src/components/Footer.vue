<script>

export default {
  name: 'Footer',

  data() {
    return {
      phone: '',
      msg: [],

    }
  },


  watch: {
    phone(value) {
      // binding this to the data value in the phone input
      this.phone = value;
      this.validatePhone(value);
    }
  },

  methods: {
    validatePhone(value) {
     if (/^[0-9]{10}$/g.test(value)) {
        this.msg['phone'] = '';
      }
      else if (/[a-zA-Z]/.test(value)) {
        this.msg['phone'] = "Το πεδίο Αριθμός Τηλεφώνου δέχεται μόνο αριθμούς"
      }
      else if (value === " " || value == null) {
        this.msg['phone'] = "Το πεδίο Αριθμός Τηλεφώνου δεν δεχεται κενα"
      }
      else {
        this.msg['phone'] = 'Ο Αριθμός Τηλεφώνου δεν είναι σωστός. Ο αριθμός θα πρέπει να περιέχει 10 χαρακτήρες.';
      }
    },

    validationOnClick: function (e) {
      if (/^[0-9]{10}$/g.test(this.phone)) {
        this.msg['phone'] = "Ευχαριστούμε για την επικοινωνία!"
      }
      else {
        let input = document.querySelector('input')

        input.classList.add('shake');
        setTimeout(() => {
          input.classList.remove('shake');
        }, 2000);
      }
    }

  }
};
</script>

<template>
  <div class="footer">
    <form @submit.prevent>
      <p>Συμπλήρωσε εδώ το τηλέφωνό σου. Θα σε καλέσουμε άμεσα.</p>
      <i class="fa-solid fa-phone"></i>
      <input class="input" placeholder="Αριθμός τηλεφώνου…" type="phone" v-model="phone" />
      <span v-if="msg.phone">{{ msg.phone }}</span>
      <button v-on:click="validationOnClick($event)">Καλεστε</button>
    </form>
  </div>
</template>

<style scoped>
div {
  padding: 0;
  position: absolute;

  bottom: -20px;
  width: 655px;
  height: 125px;
  background: #223657 0% 0% no-repeat padding-box;
  border-radius: 0px 0px 5px 5px;
  opacity: 1;
}

p {
  position: absolute;
  margin: 0;
  padding: 0;
  top: 40px;
  left: 30px;
  width: 253px;
  height: 40px;
  text-align: left;
  letter-spacing: 0px;
  color: #ffffff;
  opacity: 1;
  font-size: 15px;
  font-weight: 700;
}
i {
  z-index: 4;
  transform: scale(-1, 1);
  color: #d6d6d6;
  position: absolute;

  top: 53.3px;
  left: 325px;
  width: 18.41px;
  height: 18px;

  opacity: 1;
}
.input {
  z-index: 3;
  padding: 0;
  padding-left: 46px;
  position: absolute;
  top: 40px;
  left: 310px;
  width: 168px;
  height: 43px;
  background: #ffffff 0% 0% no-repeat padding-box;
  border: 1px solid #e4e4e4;
  border-radius: 5px 0px 0px 5px;
  opacity: 1;
}

::placeholder {
  font-size: 14px;
  font-weight: 500;
  color: #9e9e9e;
  text-align: left;
  letter-spacing: 0px;
  color: #9e9e9e;
  opacity: 1;
}

span {
  z-index: 5;
  position: absolute;
  top: 90px;
  left: 310px;
  width: 168px;
  font-size: 15px;
  font-weight: 500;
  background: #ffffff 0% 0% no-repeat padding-box;
  border-radius: 5px;
}

button {
  cursor: pointer;
  position: absolute;
  top: 40px;
  left: 525px;
  width: 100px;
  height: 45px;
  background: #55ac36 0% 0% no-repeat padding-box;
  border-radius: 0px 5px 5px 0px;
  opacity: 1;
  border: 1px solid #55ac36;
  text-align: center;
  letter-spacing: 0px;
  color: #ffffff;
  text-transform: uppercase;
  opacity: 1;
  font-size: 15px;
  font-weight: 500;
}
.shake {
  animation: shake 0.2s;
  background: orange;
}
@keyframes shake {
  0%,
  50%,
  100% {
    top: 40px;
  }
  25% {
    top: 50px;
  }
  75% {
    top: 30px;
  }
}
@media screen and (max-width: 600px) {

  p {
    top:2vh;
    width: 90vw;
    box-shadow: none;
    font-size: 100% ;
  
  
  }
  div{
    width: 100%;
    height: 25%;
    border-radius: 0;
  }
  .input {
    left:30px;
    margin-top: 3vh;
  }
  button {
    left: 246px;
    margin-top: 3vh;
  }
  i{
      left:40px;
    margin-top: 3vh;
  }
  span{
    width: 50%;
    left: 29px;
    top: 116px;
    padding: 5px;
  }


}
</style>

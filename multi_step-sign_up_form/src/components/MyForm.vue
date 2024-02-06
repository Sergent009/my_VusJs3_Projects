<template>
<div class="container">
  <div id="progress" :style="{width: progress}"></div>
  <div id="register">
    <i v-if="position === 0" class="previousButton fas fa-user"></i>
    <i v-else class="previousButton fas fa-arrow-left" @click="previousStep"></i>
    <i class="forwardButton fas fa-arrow-right" @click="checkStep"></i>
    <div id="inputContainer" :class="{'showContainer': showContainer}">
      <form @submit.prevent="checkStep">
        <input id="inputField" :type="inputType" v-model="inputValue" ref="registerinput" required />
        <label id="inputLabel"> {{ inputLabel }} </label>
      </form>
      <div id="inputProgress"></div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'myForm',

  data(){
    return{
      position: 0,
      inputLabel: '',
      inputType: 'text',
      inputValue: '',
      showContainer: false,
      progress: '0%',
      registerSteps: [{
        label: "What is Your First Name ?",
        type: "text",
        value: "",
        pattern: /.+/
      },
      {
        label: "What is Your Last Name ?",
        type: "text",
        value: "",
        pattern: /.+/
      },
      {
        label: "What is Your Email ?",
        type: "text",
        value: "",
        pattern: /^[^\s@]+@[^\s@]+\.[^\s@]+$/ 
      },
      {
         label: "Create Your Password",
        type: "text",
        value: "",
        pattern: /.+/
      }]
    }
  },

  methods: {
    setStep(){
    this.inputLabel = this.registerSteps[this.position].label
    this.inputType = this.registerSteps[this.position].type
    this.inputValue = this.registerSteps[this.position].value
    this.$refs.registerinput.focus()
    this.showStep()
    },
    showStep(){
      setTimeout(() => {
        this.showContainer = true
      })
    },

    hideStep(callback){
      this.showContainer = false;
      setTimeout(callback, 100);
    },

    previousStep(){
      this.position -= 1;
      // register.className = '';
      this.hideStep(this.setStep);
      this.setProgress()
    },

    checkStep(){
    let register = document.getElementById('register')

      if(!this.registerSteps[this.position].pattern.test(this.inputValue)){
        register.classList.add('wrong');
        register.classList.add('wronganimation')
        
        setTimeout(() => {
          register.classList.remove('wronganimation')
        }, 500);

        this.$refs.registerinput.focus();
      }
      else{
        register.className = '';
         register.classList.add('okanimation')
        
        setTimeout(() => {
          register.classList.remove('okanimation')
        }, 200);

        this.registerSteps[this.position].value = this.inputValue;
        this.position += 1;

        if(this.registerSteps[this.position]){
          this.hideStep(this.setStep)
        }
        else{
          this.hideStep(() => {
            register.className = 'close';
          })
        }
      }

      this.setProgress()
    },
    setProgress(){
      this.progress = (this.position/this.registerSteps.length * 100) + '%';
    }
  },

  mounted(){
    this.setStep()
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container{
  position: absolute;
  top: 0;
  left: 0;
  font-family: 'Noto Sans', sans-serif;
  font-size: 1rem;
  color: #333;
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: radial-gradient(#009345, #106B4E);
}

#progress{
  position: absolute;
  top: 0;
  left: 0;
  width: 0%;
  height: 100vh;
  background-color: #106B4E;
  transition: width .8s ease-in-out;
}

#register{
  position: relative;
  width: 480px;
  height: 80px;
  padding: 10px;
  background-color: #fff;
  box-shadow: 0 15px 30px rgba(0,0,0,.2),
              0 10px 10px rgba(0,0,0,.2);
}

.close{
  width: 0;
  padding: 10px 0;
  overflow: hidden;
  transition: .4s ease-in-out;
  box-shadow: 0 16px 24px 2px rgba(0, 0, 0, .2);
}

#inputContainer{
  position: relative;
  padding: 30px 20px 20px 20px;
  margin-right: 60px;
  opacity: 0;   /*to be understand*/
  transition: opacity .3s ease-in-out;
}

#inputField{
  position: relative;
  width: 100%;
  font-size: 1.35rem;
  font-weight: bold;
  outline: 0;
  background: transparent;
  box-shadow: none;
  border: none;
}

:valid + #inputLabel{
    top: 3px;
    left: 42px;
    font-size: .7rem;
    font-weight: normal;
    color: #999;
  }
  
#inputLabel{
  position: absolute;
  top: 32px;
  left: 20px;
  font-size: 1.35rem;
  font-weight: bold;
  pointer-events: none;
  transition: .2s ease-in-out;
}

#inputProgress{
  width: 0%;
  border-bottom: 6px solid #106B4E;
  transition: width .6s ease-in-out;
}

.wrong #inputProgress{
  border-color: #D93F38;
}

.showContainer{
  opacity: 1 !important;
}
#inputProgress{
  width: 100%;    
}

.previousButton{
  position: absolute;
  left: 30px;
  top: 12px;
  font-size: 1rem;
  color: #9e9e9e;
  cursor: pointer;
  z-index: 20;
}
.previousButton:hover{
  color: #009345;
}

.forwardButton{
  position: absolute;
  top: 30px;
  right: 20px;
  font-size: 3rem;
  color: #106B4E;
  cursor: pointer;
  z-index: 20;
}
.forwardButton:hover{
  color: #009345;
}

.wrong .forwardButton{
  color: #D93F38;
}
.close .forwardButton, .close .previousButton{
  color: #fff;
}

.wronganimation{
  animation: .5s linear 0s 1 wrong-animation;
}

.okanimation{
  animation: .2s linear 0s 1 ok-animation;
}

@keyframes wrong-animation {
  0% {transform: translateX(0);}
  20% {transform: translateX(-20px);}
  40% {transform: translateX(20px);}
  60% {transform: translateX(-20px);}
  80% {transform: translateX(20px);}
  100% {transform: translateX(0);}
}

@keyframes ok-animation {
  0% {transform: translateY(0);}
  50% {transform: translateY(10px);}
  100% {transform: translateY(0);}

}

</style>

<template>
<body>
  <div class="container">
    <div class="display">
      <form action="">
        <input class="input" type="text" v-model="inputNumber">
      </form>
    </div>

    <div class="buttons">

       <div class="row">
        <div class="column">
         <button @click="() => {updateDisplay('+')}" class="btns">+</button>
         <button @click="() => {updateDisplay('-')}" class="btns">-</button>
         <button @click="() => {updateDisplay('*')}" class="btns">*</button>
         <button @click="() => {updateDisplay('/')}" class="btns">/</button>
        </div>
      </div>

      <div class="row">
        <div class="column">
         <button @click="() => {updateDisplay('1')}" class="btn">1</button>
         <button @click="() => {updateDisplay('2')}" class="btn">2</button>
         <button @click="() => {updateDisplay('3')}" class="btn">3</button>
        </div>
      </div>

     <div class="row">
        <div class="column">
         <button @click="() => {updateDisplay('4')}" class="btn">4</button>
         <button @click="() => {updateDisplay('5')}" class="btn">5</button>
         <button @click="() => {updateDisplay('6')}" class="btn">6</button>
        </div>
      </div>

       <div class="row">
        <div class="column">
         <button @click="() => {updateDisplay('7')}" class="btn">7</button>
         <button @click="() => {updateDisplay('8')}" class="btn">8</button>
         <button @click="() => {updateDisplay('9')}" class="btn">9</button>
         <form action="" @submit.prevent="calculateResult()">
          <button @click="clearDisplay()" class="btnC">C</button>
          <input type="submit" class="btnEquals" value="=">
         </form>
        </div>
      </div>

    </div>
  </div>
</body>
</template>

<script>
export default {
  name: 'CalculatorProject',
  data(){
    return{
      inputNumber: '',
      result: ''
    }
  },
  methods: {
    updateDisplay(val){
      this.inputNumber = this.inputNumber + val
    },

    calculateResult(){
      // eval is a function to calculate the input strings in javaScript.
      this.result = eval(this.inputNumber)
      this.inputNumber = this.result
    },

    clearDisplay(){
      this.inputNumber = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

body{
 
  margin-left: 350px;
  margin-top: 40px;
}

.container{
  padding: 40px 50px;
  padding-left: 90px;
  border: 5px solid yellow;
  border-radius: 20px;
  width: 420px;
  background: linear-gradient(120deg, skyblue, rgb(30, 30, 141))
}

.btns{
width: 70px;
height: 70px;
margin: 10px;  
padding: 20px;
font-size: 20px;
font-weight: bold;
color:aliceblue;
background: linear-gradient(135deg, rgb(36, 93, 117), rgb(65, 65, 124));
border-radius: 10px;
}

.btn{
width: 100px;
height: 70px;
margin: 10px;  
padding: 20px;
font-size: 25px;
font-weight: bold;
color:aliceblue;
background: linear-gradient(135deg, rgb(36, 93, 117), rgb(65, 65, 124));
border-radius: 10px;
}
.btn:hover{
  background: rgb(99, 130, 143);
  cursor: pointer;
}
.btns:hover{
  background: rgb(99, 130, 143);
  cursor: pointer;
}

.btnC, .btnEquals{
  width: 150px;
  height: 50px;
  margin-right: 60px;
  margin-top: 10px;
  font-size: 25px;
  color: black;
  font-weight: bold;
  border-radius: 10px;
  background: rgb(219, 219, 44);
  cursor: pointer;
}
.btnC:hover, .btnEquals:hover{
  background: rgb(151, 151, 62);
}

.input{
  width: 360px;
  height: 55px;
  border-radius: 10px;
  margin-bottom: 25px;
  margin-right: 40px;
  border-color: rgb(133, 156, 165);
  font-size: 30px;
  color: black;
}

</style>

<template>
<div>
<div class="display">
  <input v-model.number="operand1"/>
  <input v-model.number="operand2"/>
  <input v-model.number="operand3"/>
  = {{result}}
<br/>
</div>
<div class="error">
{{error}}
</div>
<div class="keyboard">
 
  <button :title="operand" 
  v-for="operand in operands" @click ="calculate(operand)" :key="operand">
{{ operand }}
  </button>
  <button v-on:click="input(num)" v-for="num in numbers">
    {{ num }}
  </button>
  <div class="logs">
    <div class="log" v-for="(item, idx) in logs" :key="idx">
      {{ item }}
    </div>
    <input type="radio" id="one" value="Операнд 1" v-model="picked">
<label for="one">Операнд 1</label>
<br>
<input type="radio" id="two" value="Операнд 2" v-model="picked">
<label for="two">Операнд 2</label>
<br>
<span>Выбрано: {{ picked }}</span>
  </div>
</div>
<div id="application">
   <input type="checkbox" v-model="checked">
   <p>Отобразить экранную клавиатуру</p>
  </div>
</div>


</template>
<script>
export default {
  name: 'super-calculator',
  data () {
    return {
      operand1: 0,
      operand2: 0,
      operand3: 0,
      result: 0,
      error: '',
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      myCollection: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      operands: ["+", "-", "/", "*", "$"],
      
      logs: {},
      checked: '',
    };
  },
  methods: {
    
 input: function() {
     this.numbers();
     },
       calculate (operation  = '+') {
    this.error = ''
    this.checked
    switch (operation) {
      case '+':
        this.add()
        break;
    
      case '-':
        this.substract()
        break;
   
      case '/':
        this.divide()
        break;
      case '*':
        this.multiply()
        break;
        case '$':
        this.p2p()
        break;
    }
    
   
this.logs [Date.now()]= `${this.operand1} ${operation} ${this.operand2} ${this.operand3} =${this.result}`
  
},
  add () {
    this.result = +this.operand1 + +this.operand2
  },
  substract () {
    this.result = this.operand1 - this.operand2
  },
  divide () {
    this.result = this.operand1 / this.operand2
    const { operand1, operand2 } = this
    if (operand2 === 0) {
      this.error = 'Делить на 0 нельзя'
      return
    }
      this.result = operand1 / operand2
  },
  multiply () {
    this.result = this.operand1 * this.operand2
  },
  p2p () {
    this.result = this.operand3 / this.operand1 * this.operand2
  }
///// операнд1 продажа, операнд2 покупка, операнд3 сумма рублей
  },

  
    }
    
</script>


<style scoped lang="scss">

</style>

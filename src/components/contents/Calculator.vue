<template>
<div>
    <Nav></Nav>
    <div class="calculator">
    <div class="display">{{current || '0'}}</div>
    <div @click="clear" class="btn">C</div>
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="times" class="btn operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>
  <Footer></Footer>
</div>
  
</template>
<script>
import Nav from "@/components/cmm/Nav.vue"
import Footer from "@/components/cmm/Footer.vue"
export default{
	name : 'calculator',
	components : {
		Nav, Footer
  },
  data(){
    return {
      previos : null,
      current : '',
      operator : null,
      operatorClicked : false
    }
  },
  methods :{
    clear(){this.current=''},
    setPrevios(){
      this.previos = this.current
      this.operatorClicked = true
    },
    append(number){
      if(this.operatorClicked){
        this.current = '',
        this.operatorClicked = false
      }
      this.current = `${this.current}${number}`
    },
    add(){
      this.operator = (a, b) => a + b
      this.setPrevios()
    },
    minus(){
      this.operator = (a, b) => a - b
      this.setPrevios()
    },
    times(){
      this.operator = (a, b) => a * b
      this.setPrevios()
    },
    divide(){
      this.operator = (a, b) => a / b
      this.setPrevios()
    },
    equal(){
      this.current = `${this.operator(parseFloat(this.previos),
                                      parseFloat(this.current))}`
      this.previos = null
    } 
  }
}
</script>

<style scoped>
.calculator{
	margin: 0 auto;
	width : 400px;
	font-size : 40px;
	display : grid;
	grid-template-columns : repeat(4, 1fr);
	grid-auto-rows : minman(50px, auto);
}
.display{
	grid-column : 1 / 5;
	background-color : #333;
	color : white;
}
.zero{
	grid-column : 1 / 3;
}
.btn{
	background-color : #F2F2F2;
	border : 1px solid #999;
}
.operator{
	background-color : orange;
	color : white;
}
</style>
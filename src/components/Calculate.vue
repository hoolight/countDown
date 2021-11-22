<template>
  <div class="body">
    <div>
      <div>注射用乳糖酸红霉素</div>
      <input type="number" class="num1" v-model="num1" @click="clear1();"><span> ×30 <button @click="Calculate1();">=</button></span>&nbsp;<span>{{result1}}</span>
    </div>
    <div class="line_01"></div>
    <div>
      <div>注射用头孢哌酮舒巴坦</div>
      <input type="number" class="num1" v-model="num2" @click="clear2();"><span> ×80 <button @click="Calculate2();">=</button></span>&nbsp;<span>{{result2}}</span>
    </div>
    <div class="line_01"></div>
    <div>
      <div>痰热清注射液</div>
      <input type="number" class="num1" v-model="num3" @click="clear3();"><span> ×0.5 <button @click="Calculate3();">=</button></span>&nbsp;<span>{{result3}}</span>
    </div>
    <div class="line_01"></div>
    <div>
      <div>喜炎平注射液</div>
      <input type="number" class="num1" v-model="num4" @click="clear4();"><span> ×0.4 <button @click="Calculate4();">=</button></span>&nbsp;<span>{{result4}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculate",
  data(){
    return {
      num1:'',
      num2:'',
      num3:'',
      num4:'',
      result1:'',
      result2:'',
      result3:'',
      result4:'',
    }
  },
  methods:{
    clear1(){
      this.num1=''
    },
    clear2(){
      this.num2=''
    },
    clear3(){
      this.num3=''
    },
    clear4(){
      this.num4=''
    },
    Calculate1(){
      this.result1 = this.accMul(this.num1,30)
    },
    Calculate2(){
      this.result2 = this.accMul(this.num2,80)
    },
    Calculate3(){
      this.result3 = this.accMul(this.num3,0.5)
    },
    Calculate4(){
      this.result4 = this.accMul(this.num4,0.4)
    },
    accMul(arg1, arg2) {
      let m = 0, s1 = arg1.toString(), s2 = arg2.toString();
      try { m += s1.split(".")[1].length } catch (e) { console.log(e) }
      try { m += s2.split(".")[1].length } catch (e) { console.log(e) }

      return Number(s1.replace(".", "")) * Number(s2.replace(".", "")) / Math.pow(10, m);
    }
  }
}
</script>

<style scoped>
  .num1 {
    width: 50px;
  }
  .body {

  }
  .line_01{
    padding: 0 20px 0;
    margin: 20px 0;
    line-height: 2px;
    border-left: 190px solid #ddd;
    border-right: 190px solid #ddd;
    text-align: center;
  }
</style>
<template>

  <div id="hellow">
    
    <label for="l_inr">INR: Rs: </label>
    <input id="l_inr" type="text" v-model="getINR">
    <input type="button" name="button" value="Convert to USD" @click="convertCurr('USD')"/><!--convertINR / convertCurr()-->
    
    <label for="l_usd">USD: $: </label>
    <input id="l_usd" type="text" v-model="getUSD"> 
    <input type="button" name="button" value="Convert to INR" @click="convertCurr('INR')" /><!--convertUSD / convertCurr()-->    
    
    <div id="head_inr">INR: Rs: {{getINR}}</div>
    <div id="head_usd">USD: $: {{getUSD}}</div>
    
    
  </div>

</template>

<script>
export default {
  data () {
    return {      
      getINR: "",
      getUSD: "",
      result: "",
    }    
  },
  methods: { 
    convertCurrUSD () {
        this.getUSD = this.getINR / 72.95
    },
    convertCurrINR () {
        this.getINR = this.getUSD * 72.95
    },
    convertCurr (flag) {      
      const inr_element = document.getElementById("l_inr");
      if(typeof inr_element !== "undefined" && inr_element.value !== ''){
        if (flag == 'INR') {
            let result = this.getUSD*72.95 
          this.getINR = result
        } else {
            let result = this.getINR/72.95
            this.getUSD = result
        }        
      }else{
        alert("You must enter INR value")
      }      
    },    
  }  
}
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
#l_inr, #l_usd{
  margin: 10px 5px;
}
label{
  margin-left: 10px;
}
</style>
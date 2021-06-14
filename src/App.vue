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
    <hr>

    <h1>This one has watchers</h1>
    <label for="l_inr">Watch INR: Rs: </label>
    <input id="l_inr" type="text" v-model="watchCurrINR">
    
    <label for="l_usd">Watch USD: $: </label>
    <input id="l_usd" type="text" v-model="watchCurrUSD">    
    
  </div>

</template>

<script>
export default {
  data () {
    return {      
      getINR: "",
      getUSD: "",
      watchCurrINR: "",
      watchCurrUSD: ""
    }    
  },
  methods: { 
    convertCurrUSD () {
        this.getUSD = this.getINR / 72.95
        console.log("Result is: ", this.getUSD)
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
  },
  watch: {
    watchCurrINR(newVal, oldVal){
      console.log("This is new val: ", newVal);
      console.log("This is old val: ", oldVal);

      oldVal = newVal/72.95
      this.watchCurrUSD = oldVal
      console.log("This is USD val: ", oldVal);      
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
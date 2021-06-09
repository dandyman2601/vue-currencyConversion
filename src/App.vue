<template>

  <div id="hellow">
    
    <label for="l_inr">INR:</label>
    <input id="l_inr" type="text" v-model="getINR">
    <input type="button" name="button" value="Convert to USD" @click="convertCurr()"/><!--convertINR / convertCurr()-->
    
    <label for="l_usd">USD:</label>
    <input id="l_usd" type="text" v-model="getUSD"> 
    <input type="button" name="button" value="Convert to INR" @click="convertCurr()" /><!--convertUSD / convertCurr()-->    
    
    <div id="head_inr"></div>
    <div id="head_usd"></div>
    
    
  </div>

</template>

<script>
export default {

  data () {
    return {      
      getINR: "",
      getUSD: "",
    }
    
  },

  methods: { 
    // convertINR () {
    //   if(typeof document.getElementById("l_usd").value !== "undefined" && document.getElementById("l_usd").value !== ''){
    //     var result = this.getINR/72.95
    //     document.getElementById("l_usd").value = result      
    //     document.getElementById("head_inr").innerHTML = `<h1>INR: Rs ${this.getINR}</h1>`
    //     document.getElementById("head_usd").innerHTML = `<h1>USD: $ ${result}</h1>`
    //     console.log("INR: " + this.getINR)
    //     console.log("USD: "+ this.getUSD)
    //     console.log(result)
    //   }else{
    //     alert("You must enter INR value")
    //   }
    // },
    // convertUSD () {
    //   var result = this.getUSD*72.95 
    //   document.getElementById("l_inr").value = result
    //   document.getElementById("head_inr").innerHTML = `<h1>INR: Rs ${result}</h1>`
    //   document.getElementById("head_usd").innerHTML = `<h1>USD: $ ${this.getUSD}</h1>`
    //   console.log("INR: " + this.getINR)
    //   console.log("USD: "+ this.getUSD)
    //   console.log(result)

    // },
    convertCurr () {
      const inr_element = document.getElementById("l_inr");
      const usd_element = document.getElementById("l_usd");

      if(typeof inr_element !== "undefined" && inr_element.value !== ''){
        
        if(inr_element){
          let result = this.getUSD*72.95 
          inr_element.value = result          
          usd_element.value = this.getUSD
        }

        if(usd_element){
          let result = this.getINR/72.95
          usd_element.value = result                 
          inr_element.value = this.getINR        
        }

        document.getElementById("head_inr").innerHTML = `<h1>INR: Rs ${inr_element.value}</h1>`
        document.getElementById("head_usd").innerHTML = `<h1>USD: $ ${usd_element.value}</h1>`
        console.log("inr_element: " + inr_element.value)
        console.log("usd_element  " + usd_element.value)
      }else{
        alert("You must enter INR value")
      }      
    },    
  },  

  beforeCreate () {
    console.log("beforeCreate")
  },
  created () {
    console.log("created")
  },
  mounted () {
    console.log("mounted")

    setTimeout(() => {
      this.age = 88;
    }, 3000)
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
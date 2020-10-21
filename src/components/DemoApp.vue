<template>
    <div id="demo">
      <button >
            <h1 class='nameLogo'>Bank Name</h1>
            <div class="main-menubar">Menu pane</div>
            <div class="container">
            <div class="steps" >
                <button @click="sendAlert" class="btn btn-outline-success step-space">step1</button>
                <button class="btn btn-outline-success step-space">step2</button>
                <button class="btn btn-outline-success step-space">step3</button>
                <button class="btn btn-outline-success step-space">step4</button>
                <button class="btn btn-outline-success step-space">step5</button>
            </div>
            <div class=''>
                <div>
                    <label class='inputlbl' for="income">Income* :</label>
                    <input class="iptb" type="number" v-model="income" >
                    <label class='inputlbl-unit' for="totalValue">€</label>
                </div>
                <div>
                    <label  class='inputlbl' for="totalValue">Tenure* :</label>
                    <input class="iptb" type="number" v-model="tenure" >
                    <label class='inputlbl-unit' for="totalValue">Months</label>
                </div>
                <div class="slidecontainer">
                    <label class='inputlbl' for="Interest">Interest % :</label>
                    <input type="range" min="1" max="100" v-model= "sliderValue" class="slider" id="myRange">
                </div>
                <div>
                    <label for="Slider value" >{{sliderValue}} %</label>
                </div>
                <div>
                    <label class='resultlbl' for="totalValue">Eligible Amount:</label>
                    <label for="TotalAmount">{{eligibleAmount}} €</label>
                </div>
                <div>
                    <label class='resultlbl' for="totalValue">Total Payable Amount:</label>
                    <label for="TotalAmount">{{totalAmount}} €</label>
                </div>
            </div>
         </div>
        </div>
</template>

<script>
export default {

  name: 'DemoApp',
  data: function () {
    return {
      sliderValue: 1,
      income: 0,
      tenure: 0,
      eligibleAmount: 0,
      totalAmount: 0
    }
  },
  watch: {
    sliderValue: function () {
      console.log('slidervaluechange')
      this.eligibleAmt()
    },
    income: function () {
      console.log('IncomeChange')
      this.eligibleAmt()
    },
    tenure: function () {
      console.log('tenureChange')
      this.eligibleAmt()
    }
  },

  methods: {
    sendAlert () {
      alert('working!')
    },
    eligibleAmt () {
      this.eligibleAmount = this.income / 2 * this.tenure
      this.totalAmt()
      return (this.eligibleAmount)
    },
    totalAmt () {
      this.totalAmount = this.eligibleAmount + this.eligibleAmount * (this.sliderValue / 100)
      return (this.totalAmount)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
/* layout */
.nameLogo{
    color: grey;
    margin-left: 4em;
}
.inputlbl{
    font-size: 16px;
    color: #004c4c;
    margin: -2px 0 14px;
    padding-top: 24px;
    clear: both;
    font-family: 'Roboto Condensed', Arial, Helvetica, sans-serif;
}
.resultlbl{
    font-size: 20px;
    font-weight: 600;
    color: #004c4c;
    margin: -2px 0 14px;
    padding-top: 24px;
    clear: both;
    font-family: 'Roboto Condensed', Arial, Helvetica, sans-serif;
}
.inputlbl-unit{
    margin-left: 10px;
}
.main-menubar{
    /* position: absolute; */
    z-index: -1;
    top: -36px;
    display: block;
    /* content: ''; */
    width: 100%;
    height: 36px;
    background: #009286;
    color: white;
    padding-left: 10em;
    padding-top: 2px;
}
.steps{
    margin-top: 20px;
}
.step-space{
    margin-left:10px;
}
.iptb{
    margin-top: 20px;
    margin-left: 10px;
}
/* custom slide */
  .slidecontainer {
    width: 50%; /* Width of the outside container */
    margin-top: 20px;
}
  .slider {
    -webkit-appearance: none;
    width: 100%;
    height: 15px;
    border-radius: 5px;
    background: #d3d3d3;
    outline: none;
    opacity: 0.7;
    -webkit-transition: .2s;
    transition: opacity .2s;
}

  .slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 25px;
    height: 25px;
    border-radius: 50%;
    background: #1ebefb;
    cursor: pointer;
}

  /* Mouse-over effects */
  .slider:hover {
    opacity: 1; /* Fully shown on mouse-over */
}

  .slider::-moz-range-thumb {
    width: 25px;
    height: 25px;
    border-radius: 50%;
    background: #1ebefb;
    cursor: pointer;
}
</style>

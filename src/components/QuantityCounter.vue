<template>
  <div id="QuantityCounter">
    <h1> Exercise 1 </h1>
    <button class= "button button" @click = "decrementCounter"> 
        - </button>
    <span> {{ counter }} </span>
    <button class= "button button" @click = "incrementCounter"> 
      + </button>
  </div>
</template>

<script>

export default {
  name: 'QuantityCounter',
  props: {
      item: Object
  },
  data() {
    return {
      title: 'Counter',
      counter: 0
    }
  }, 
  methods: {
    incrementCounter() {
      if (this.counter < 10) {
        this.counter++;
        this.$emit('counter', this.item, this.counter);
      } else {
        alert("You can't buy more than 10 items!")
        this.$emit('counter', this.item, this.counter);
      }
      
    }, 
    
    decrementCounter() {
      if (this.counter > 0) {
        this.counter--;
        this.$emit('counter', this.item, this.counter);
      } else {
        this.counter = 0;
        this.$emit('counter', this.item, this.counter);
      }
    },


    }
  }

</script>

<style scoped>
.button {
  background-color: #008CBA;
  color: white;
  padding: 8px 16px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 20px;
  margin: 2px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
  border-radius: 10px;
  box-shadow: 0 8px 16px 0 rgba(43, 99, 184, 0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
}


.button:hover {
  
  background-color: white; /* Green */
  border: 2px solid #008CBA;
  color:  black;
}


</style>


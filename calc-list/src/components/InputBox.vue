<template>
  <div class="calculator">
    <h1>{{ firstNumber }}</h1>
    <h3 v-show="showInputText"> {{ inputText}} </h3>
    <input type="text" v-model="inputNumber" id="box" :placeholder="placeHolderText"/>
    <input type="button" v-on:click="plus()" value="+"/>
  </div>
</template>

<script>
export default {
  name: 'InputBox',
  props: {
    msg: {
      type: String,
      required: false,
    }
  },
  data: function() {
    return {
      inputNumber: "",
      firstNumber: 0,
      inputText: "",
      placeHolderText: 'Enter the first number',
      plusDisabled: false,
      showInputText: false,
    }
  },
  methods: {
    plus: function() {
      if(this.inputText) {
        this.showInputText = true;
        this.inputText = this.inputText + "+" + this.inputNumber;
      } else {
        this.inputText = this.inputNumber;
      }
      this.firstNumber = parseFloat(this.firstNumber) + parseFloat(this.inputNumber);
      this.placeHolderText = 'Enter the second number',
      this.inputNumber = ""
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<template>
  <div class="calculator">
    <h1>{{ firstNumber }}</h1>
    <h3 v-show="showInputText"> {{ inputText}} </h3>
    <input type="text" v-model="inputNumber" id="box" :placeholder="placeHolderText"/>
    <input type="button" v-on:click="validate(inputNumber) ? add() : setError()" value="+"/>
    <input type="button" v-on:click="validate(inputNumber) ? subtract(): setError()" value="-"/>
    <input type="button" v-on:click="validate(inputNumber) ? multiply(): setError()" value="*"/>
    <input type="button" v-on:click="validate(inputNumber) ? divide(): setError()" value="/"/>

    <p v-show="showErrorText"> Input has to be a number </p>
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
      showErrorText: false,
    }
  },
  methods: {
    add: function() {
      if(this.inputText) {
        this.showInputText = true;
        this.inputText = this.inputText + "+" + this.inputNumber;
      } else {
        this.inputText = this.inputNumber;
      }
      this.firstNumber = parseFloat(this.firstNumber) + parseFloat(this.inputNumber);
      this.placeHolderText = 'Enter the second number';
      this.inputNumber = "";
      this.showErrorText = false;
    },
    subtract: function() {
      if(this.inputText) {
        this.showInputText = true;
        this.inputText = this.inputText + "-" + this.inputNumber;
      } else {
        this.inputText = this.inputNumber;
      }
      this.firstNumber = parseFloat(this.firstNumber) - parseFloat(this.inputNumber);
      this.placeHolderText = 'Enter the second number';
      this.inputNumber = "";
    },
    multiply: function() {
      if(this.inputText) {
        this.showInputText = true;
        this.inputText = this.inputText + "*" + this.inputNumber;
      } else {
        this.inputText = this.inputNumber;
      }
      this.firstNumber = parseFloat(this.firstNumber) * parseFloat(this.inputNumber);
      this.placeHolderText = 'Enter the second number';
      this.inputNumber = "";
      this.showErrorText = false;
    },
    divide: function() {
      if(this.inputText) {
        this.showInputText = true;
        this.inputText = this.inputText + "/" + this.inputNumber;
      } else {
        this.inputText = this.inputNumber;
      }

      if(!parseFloat(this.inputNumber)) {
        this.placeHolderText = 'Cannot divide a number by zero.',
        this.inputNumber = "";
      } else {
        this.firstNumber = parseFloat(this.firstNumber) / parseFloat(this.inputNumber);
        this.placeHolderText = 'Enter the second number';
        this.inputNumber = "";
      }
      this.showErrorText = false;
    },
    validate: function(input) {
      var boxedInput = parseFloat(input);
      if(boxedInput) {
        return true;
      }

      return false;
    },
    setError: function() {
      this.showErrorText = true;
    }

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

<template>
  <div id="app">
    <h4>option: numeric and max:length</h4>
    <p>
      <input v-validate="'numeric|max:10'" type="text" name="num1">
      <br>
      <span v-if="errors.has('num1')">{{ errors.first('num1') }}</span>
    </p>

    <h4>option: numeric and max_value:value</h4>
    <p>
      <input v-validate="'max_value:10'" type="text" name="num2">
      <br>
      <span v-if="errors.has('num2')">{{ errors.first('num2') }}</span>
    </p>

    <h4>option: Regex: ^([0-9]+)$</h4>
    <p>
      <input v-validate="{ required: true, regex: /^([0-9]+)$/ }" name="regex">
      <br>
      <span v-if="errors.has('regex')">{{ errors.first('regex') }}</span>
    </p>

    <h4>test</h4>
    <input type="text" @input="addEvent" v-model="input">
    <p>{{ text }}</p>

    <button @click="register">Register</button>
  </div>

</template>

<script>
  import Vue from 'vue'
  import VeeValidate from 'vee-validate'

  Vue.use(VeeValidate)

  export default {
    data() {
      return {
        input: '',
        text: ''
      }
    },
    methods: {
      register() {
        // this.$validator.validateAll().then(() => {
        //   alert('Hello, ' + this.email)
        // }).catch(() => {
        //   alert(this.errors.all())
        // })
      },
      addEvent: function (e) {
        // e.preventDefault()
        if (this.isValid) {
          this.text += this.input
        }else{
          console.log("need edit")
        }
        this.input = ''
      },
    },
    computed: {
      isValid: function () {
        // 省略
        return true
      }
    }
  }
  new Vue({

  });
</script>

<style>
  .alert-danger {
    color: red;
  }

  .has-error {
    border-color: red;
  }
</style>

<template>
  <div id="app">
    <input type="text" v-model="number">
    <button @click="push">住所自動入力</button>
    <p>Address：{{name}}</p>
  </div>
</template>
<script>
import axios from "axios"
export default {
  data(){
    return{
      number: "",
      name: ""
    }
  },
  methods: {
    push() {
      axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.number}?apiKey=HkxyMitjcUp3biK3xWHQunXt1qKfqjbBXdIyuhf`).then(response => {
        console.log(response.data[0].allAddress);
        this.name = response.data[0].allAddress;
      })
    }
  }
}
</script>
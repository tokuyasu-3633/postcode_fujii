<template>
  <div id="app">
    <input type="text" v-model="number">
    <p>{{number}}</p>
    <p>{{allAdress}}</p>
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
      allAdress: "",
      name: ""
    }
  },
  async created() {
    const item = await axios.get(`https://apis.postcode-jp.com/api/v4/postcodes/${this.number}?apiKey=HkxyMitjcUp3biK3xWHQunXt1qKfqjbBXdIyuhf`);
    const data = item.prefCode;
    this.allAdress = data;
  },
  methods: {
    push() {
      this.name = this.allAdress;
    }
  }
}
</script>
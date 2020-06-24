<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="url">
    <input type="button" value="Convert" v-on:click="convert(url)">
    <div class="qr-image">
      <img :src="imgSrc" v-if="url !== ''">
      <h3 v-else>This is where your image will load.</h3>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Main',
    props: {
      msg: String
    },
    data () {
      return {
        url: '',
        imgSrc: ''
      }
    },
    methods: {
      convert: function(url) {
        const QR_URL = `https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=${url}`;
        this.imgSrc = QR_URL;
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
  .qr-image {
    margin: 20px 0 0 0;
  }
</style>

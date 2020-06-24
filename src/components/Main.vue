<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input type="text" v-model="url">
    <input type="button" value="Convert" v-on:click="convert(url)">
    <img :src="url" alt="The QR code">
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
        url: ''
      }
    },
    methods: {
      convert: function(url) {
        const QR_URL = `https://qrtag.net/api/qr(_transparent)(_100x100).png(?url=${url})`;
        this.url = QR_URL;
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

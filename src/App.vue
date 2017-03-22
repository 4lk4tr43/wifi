<template>
  <div id="app">
    <wifi v-for="(item, index) in items"
           v-bind:data="item"
           v-bind:key="item.mac">
    </wifi>
  </div>
</template>

<script>
import Wifi from './components/Wifi'

export default {
  name: 'app',
  data() {
    return {
        items: [
          {
            ssid: "Network 1",
            mac: "12:34:56:78",
            quality: 50,
            signal: -60,
            encryption: true,
            encryptionType: "wpa2",
            password: "123123",
            connected: false
          }
        ]
    }
  },
  components: {
    Wifi
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

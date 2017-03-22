<template>
  <div class="wifi-network">
    <span class="area">
      <div class="ssid">{{ data.ssid }}</div>
      <div class="mac">{{ data.mac }}</div>
    </span>
    <span class="area" v-if="data.encryption">
      <div class="encryption">{{ data.encryptionType}}</div>
      <div class="password">
        <label>
          Passwort
          <input  v-model="data.password" type="text" />
        </label>
      </div>
    </span>
    <span class="area">
      <button class="connect">verbinden</button>
    </span>
    <span class="area">
      <performance-gauge :data-value="data.quality" data-start-color="220,20,60" data-end-color="50,205,50"></performance-gauge>
      <div class="signal">{{ data.signal }} dB</div>
    </span>
  </div>
</template>

<script>
  import PerformanceGauge from './PerformanceGauge.vue'
  export default {
    name: 'wifi',
    props: ['data'],
    components: {
        PerformanceGauge
    }
  }
</script>

<style scoped>
  .wifi-network {
    display: flex;
    margin: 4px 12px;
    padding: 12px;
    border: 1px solid black;
    border-radius: 4px;
    box-shadow: 4px 4px 4px darkgrey;
    justify-content: space-around;
  }
  .area {
    margin: 0 20px;
  }
  .ssid, .quality {
    font-size: x-large;
  }
  .mac, .signal {
    font-size: x-small;
  }
  .connect {
    height: 100%;
    width: 150px;
  }
  .encryption {
    text-align: right;
    font-size: x-small;
    margin-bottom: -12px;
    margin-top: 4px;
  }
  .password label {
    text-align: left;
    float: left;
    width: 100%;
  }
  .password label input{
    display: block;
  }
</style>

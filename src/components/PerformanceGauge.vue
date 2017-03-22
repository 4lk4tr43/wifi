<template>
    <div class="performance-gauge" :style="style">
      {{ dataValue }}%
    </div>
</template>

<script>
    export default {
        name: 'performance-gauge',
        data () {
            return {
            }
        },
        computed: {
            style: function() {
              var c1 = this.dataStartColor.replace(/\s/, '').split(',');
              var c2 = this.dataEndColor.replace(/\s/, '').split(',');
              var v = this.dataValue / 100.0;
              var r = Math.round((1 - v) * parseFloat(c1[0]) + v * parseFloat(c2[0]));
              var g = Math.round((1 - v) * parseFloat(c1[1]) + v * parseFloat(c2[1]));
              var b = Math.round((1 - v) * parseFloat(c1[2]) + v * parseFloat(c2[2]));
              return 'background-color:rgb(' + r + ',' + g + ',' + b + ');';
            }
        },
        props: ['data-value', 'data-start-color', 'data-end-color']
    }
</script>

<style scoped>
  .performance-gauge {
    color: white;
    padding: 8px;
    border-radius: 50%;
  }
</style>

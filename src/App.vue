<template>
  <div :class="$style.count_container">
    <h1 :class="$style.count_heading"></h1>
    <p :class="$style.count_value">{{ defaultNum }}</p>
    <ul :class="$style.button_list">
      <li :class="$style.count_increase" @click="increaseNum()">zvýšit</li>
      <li :class="$style.count_decrease" @click="decreaseNum()">snížit</li>
      <li :class="$style.count_reset" @click="resetNum()">reset</li>
    </ul>
    <p :class="$style.count_warning">{{ warnMes }}</p>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue';
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'App',
  setup() {
    var defaultNum = ref(0);
    var warnMes = ref('');

    function increaseNum() {
      defaultNum.value++;
      warnMes.value = '';
    }
    function decreaseNum() {
      if (defaultNum.value == 0) {
        warnMes.value = 'Nelze snížit do mínusu';
      } else {
        defaultNum.value--;
      }
    }
    function resetNum() {
      defaultNum.value = 0;
      warnMes.value = '';
    }
    return {
      defaultNum,
      warnMes,
      increaseNum,
      decreaseNum,
      resetNum,
    };
  },
});
</script>

<style lang="scss" module>
$primaryCol: #fff;
$secondaryCol: #000;

$tercialyCol: darkorchid;
$quaternalyCol: purple;
html {
  margin: 0;
  padding: 0;
  background: $secondaryCol;
}
.count_container {
  width: 300px;
  margin: 30px auto 0 auto;
}
.count_heading {
  font-size: 20px;
  text-align: center;
}
.count_value {
  text-align: center;
  font-size: 28px;
  color: $primaryCol;
}
.button_list {
  list-style: none;
  padding: 0;
  margin: 0;
  width: 100%;
}
.count_increase,
.count_decrease,
.count_reset {
  width: 100%;
  height: 30px;
  color: #fff;
  font-size: 16px;
  text-align: center;
  margin: 10px 0;
  border-radius: 20px;
  line-height: 1.8;
  background: $quaternalyCol;
  &:hover {
    background: $tercialyCol;
  }
}
.count_warning {
  color: $tercialyCol;
  text-align: center;
}
</style>

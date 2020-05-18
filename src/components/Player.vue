<template>
  <div class="player">
    <div class="dics">
      唱片
    </div>
    <div class="vol">
      <van-slider v-model="value" :step="10" />
    </div>
    <div class="controls">
      <van-row>
        <van-col><van-button type="default">prev</van-button></van-col>
        <van-col><van-button type="default">play/pause</van-button></van-col>
        <van-col><van-button type="default">next</van-button></van-col>
      </van-row>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import { Col, Row, Icon, Button, Slider } from "vant";
Vue.use(Col)
  .use(Row)
  .use(Icon)
  .use(Button)
  .use(Slider);
export default {
  name: "Player",
  props: {
    msg: String,
  },
  data: function() {
    return {
      value: 50,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less"></style>

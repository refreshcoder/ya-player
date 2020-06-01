<template>
  <div class="player">
    <audio src="../assets/audio/test.mp3" controls preload>您的浏览器不支持 audio 标签。</audio>
    <div class="dics">唱片</div>
    <div class="vol">音量</div>
    <div class="controls">控制</div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Player",
  props: {
    msg: String
  },
  data: function() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less"></style>

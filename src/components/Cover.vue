<template>
  <div class="cover-outer">
    <div class="cover" ref="cover">
      <div class="cover-inner" :class="{circle:isCircle}">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    defaultType: String
  },
  data() {
    return {
      isCircle: this.defaultType==="circle" ? true : false,
    };
  },
  methods: {
    
  },
  mounted() {}
};
</script>

<style lang="less" scoped>
@import (reference) "../assets/less/variables.less";
.cover-outer {
  box-sizing: border-box;
  width: 100%;
  position: relative;
  overflow: hidden;
  .cover {
    box-sizing: border-box;
    width: 100%;
    padding: 50% 0 50% 0;
    .cover-inner {
      box-sizing: border-box;
      width: 100%;
      height: 100%;
      margin: auto;
      padding: 10px;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      position: absolute;
      background-color: @primary-color;
      img {
        width: 100%;
        height: 100%;
      }
    }
    .circle{
      animation: run 20s linear infinite both;
      border-radius: 50%;
      img{
        border-radius: 50%;
      }
    }
  }
}

@keyframes run {
  from{transform:rotate(0deg)}
  to{transform:rotate(360deg)}
}
</style>
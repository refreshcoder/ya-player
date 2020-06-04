<template>
  <div class="slider" ref="slider" @touchstart="touchstartHandler">
    <div class="slider-wrapper">
      <div class="slider-bar" :style="{width:`${value}%`}"></div>
      <span class="slider-point" ref="sliderPoint" :style="{left:`${value}%`}"></span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    defaultValue: Number
  },
  data() {
    return {
      value: this.defaultValue
    };
  },
  methods: {
    touchstartHandler(event) {
      if (event.target.nodeName !== "SPAN") {
        const width = this.$refs.slider.offsetWidth;
        const deltaX =
          event.targetTouches.item(0).clientX - this.$refs.slider.clientLeft;
        const percent = (deltaX / width).toFixed(2) * 100;
        this.value = percent;
        this.$emit("click", this.value);
      } else {
        event.target.addEventListener("touchmove", this.touchmoveHandler);
        event.target.addEventListener("touchend", this.touchendHandler);
      }
    },
    touchmoveHandler(event) {
      const width = this.$refs.slider.offsetWidth;
      const deltaX =
        event.targetTouches.item(0).clientX - this.$refs.slider.clientLeft;
      if (deltaX >= 0 && deltaX <= width) {
        const percent = (deltaX / width).toFixed(2) * 100;
        this.value = percent;
      }
    },
    touchendHandler(event) {
      this.$emit("touch", this.value);
      event.target.removeEventListener("touchmove", this.touchmoveHandler);
      event.target.removeEventListener("touchend", this.touchendHandler);
    }
  }
};
</script>

<style lang="less" scoped>
@import (reference) "../assets/less/variables.less";
.slider {
  width: 100%;
  height: 0.2rem;
  margin: 0.4rem auto;
  background-color: @disable-color;
  .slider-wrapper {
    height: 0.2rem;
    margin-right: 1rem;
    position: relative;
    .slider-point {
      display: block;
      box-sizing: border-box;
      width: 1rem;
      height: 1rem;
      margin: auto;
      border-radius: 50%;
      background-color: @background-color;
      border: 0.2rem solid @primary-color;
      position: absolute;
      top: 0;
      bottom: 0;
    }
    .slider-bar {
      width: 0;
      height: 100%;
      background-color: @primary-color;
    }
  }
}
</style>
<template>
  <div class="swiper-wrapper" @touchmove="touchmoveHandler" @touchend="touchendHandler">
    <div class="swiper">
      <slot></slot>
      <span>{{number}}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      prevT: null,
      prevX: null,
      delay: 100,
      speed: 2,
      number: 1
    };
  },
  methods: {
    touchmoveHandler(event) {
      const nowT = new Date().getTime();
      const nowX = event.targetTouches.item(0).clientX;
      if (this.prevX && this.prevT) {
        if (nowT - this.prevT >= this.delay) {
          const speed = (nowX - this.prevX) / this.delay;
          console.log(nowX,this.prevX,speed)
          if (speed >= this.speed) {
            this.number++;
          } else if (~speed >= this.speed) {
            this.number--;
          }
          this.prevT = null;
          this.prevX = null;
        }
      } else {
        this.prevX = nowX;
        this.prevT = nowT;
      }
    },
    touchendHandler() {
      this.prevT = null;
      this.prevX = null;
    }
  },
  created() {}
};
</script>

<style lang="less" scoped>
.swiper-wrapper {
  height: 40px;
  background-color: gray;
  .swiper {
    width: 100%;
    height: 100%;
  }
}
</style>
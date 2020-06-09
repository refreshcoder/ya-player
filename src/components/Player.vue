<template>
  <div>
    <Swiper></Swiper>
    <audio src="../assets/audio/UEHWUT2384FH9VWEQ3423F4.mp3" ref="audio" controls></audio>
    <Cover defaultType="circle">
      <img src="../assets/image/cover.jpg">
    </Cover>
    <Slider :defaultValue="50" @click="sliderClickHandler" @touch="sliderTouchHandler"></Slider>
  </div>
</template>

<script>
import Cover from "./Cover";
import Slider from "./Slider";
import Swiper from "./Swiper";
export default {
  components: {
    Cover,
    Slider,
    Swiper
  },
  data() {
    return {
      control: {
        //音量
        volume: 0.5,
        //静音
        muted: false,
        //播放速度
        playbackRate: 1,
        //自动播放
        autoplay: false,
        //循环播放
        loop: "loop",
        //预加载
        preload: "auto"
      }
    };
  },
  watch: {
    //监听contorl数据变化 同步至audio元素
    control: {
      handler: function() {
        const keys = Object.keys(this.control);
        keys.map(key => {
          if (key === "volume") {
            this.$refs.audio[key] = this.control[key].toFixed(1) - 0;
          } else {
            this.$refs.audio[key] = this.control[key];
          }
        });
      },
      deep: true
    }
  },
  methods: {
    //初始化audio元素属性
    init() {
      const keys = Object.keys(this.control);
      keys.map(key => {
        this.$refs.audio[key] = this.control[key];
      });
    },
    //slider点击事件
    sliderClickHandler(value) {
      this.control.volume = (value / 100).toFixed(1) - 0;
    },
    //slider滑动事件
    sliderTouchHandler(value) {
      this.control.volume = (value / 100).toFixed(1) - 0;
    }
  },
  created() {},
  mounted() {
    this.init();
  }
};
</script>

<style lang="less" scoped>
@import (reference) "../assets/less/variables.less";
</style>
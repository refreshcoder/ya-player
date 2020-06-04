<template>
  <div>
    <audio src="../assets/audio/UEHWUT2384FH9VWEQ3423F4.mp3" ref="audio" controls></audio>
    <Slider :defaultValue="50" @click="sliderClickHandler" @touch="sliderTouchHandler"></Slider>
    <!-- <div class="vol" ref="vol" @touchstart="volMousedownHandler">
      <div class="vol-wrapper">
        <div class="vol-slider-bar" :style="{width:`${control.volume*100}%`}"></div>
        <span
          class="vol-slider"
          ref="volSlider"
          :style="{left:`${control.volume*100}%`}"
        ></span>
      </div>
    </div>-->
  </div>
</template>

<script>
import Slider from "./Slider";
export default {
  components: {
    Slider
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
        autoplay: true,
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
</style>
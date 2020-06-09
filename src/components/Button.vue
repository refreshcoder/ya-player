<template>
  <div class="btn-wrapper" @click="clickHandler">
    <div class="btn">
      <div class="btn-inner">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods:{
    clickHandler(){
      this.$emit.on('click')
    }
  }
}
</script>

<style lang="less" scoped>
.btn-wrapper{
  .btn{
    padding: 0.1rem 0.2rem;
  }
}
</style>
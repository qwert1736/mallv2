<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name: 'Scroll',
  props: {
    probeType: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      scroll: null
    }
  },
  methods: {
    scrollTo(x, y, time=400) {
      this.scroll.scrollTo(x, y, time)
    }
  },
  mounted() {
    this.scroll = new BScroll(this.$refs.wrapper, {
      click: true,
      probeType: this.probeType,
      // pullUpLoad: true
    })

    this.scroll.on('scroll', position => {
      // console.log(position);
      this.$emit('scroll', position)
    })
    // this.scroll.on('pullingUp', () => {
    //   console.log('上拉加载更多');
    // })
  }
}
</script>

<style>

</style>
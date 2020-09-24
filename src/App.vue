<template>
  <div id="app">
    <transition :name="transitionName">
      <router-view/>
    </transition>
  </div>
</template>

<script>
export default {
  data () {
    return {
      transitionName: 'slide-left'
    }
  },
  watch: {
    $route (to, from) {
      // 有主级到次级
      if (to.meta.index > from.meta.index) {
        this.transitionName = 'slide-left' // 向左滑动
      } else if (to.meta.index < from.meta.index) {
        // 由次级到主级
        this.transitionName = 'slide-right'
      } else {
        this.transitionName = ''
      }
    }
  }
}
</script>

<style lang="less">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  .router-view {
    width: 100%;
    height: auto;
    position: absolute;
    top: 0;
    bottom: 0;
    margin: 0 auto;
    -webkit-overflow-scrolling: touch;
  }

  .slide-right-enter-active,
  .slide-right-leave-active,
  .slide-left-enter-active,
  .slide-left-leave-active {
    transition: all 500ms;
    position: absolute;
    backface-visibility: hidden;
  }

  .slide-right-enter {
    opacity: 0;
    transform: translate(-100%, 0);
  }

  .slide-right-leave-to {
    opacity: 0;
    transform: translate(100%, 0)
  }

  .slide-left-enter {
    opacity: 0;
    transform: translate(100%, 0);
  }

  .slide-left-leave-to {
    opacity: 0;
    transform: translate(-100%, 0);
  }
}
</style>

<template>
  <div class="home">
    <van-button type="primary">默认按钮</van-button>
    <i class="icon-font icon007-detective"></i>
    <p>你好</p>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {}
}
</script>

<style lang="less">
.home {
  color: red;

  p {
    font-size: 75px;
  }

  i {
    font-size: 18px;
  }
}
</style>

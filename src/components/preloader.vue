<template>
  <div class="preloader w-100 blue h-100">
    <div class="preloader-content"></div>
  </div>
</template>

<script>
export default {
  name: 'preloader',
}
</script>

<style lang="scss">
.preloader {
  position: relative;
  .preloader-content {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 144px;
    height: 144px;
    margin-left: 0px - (144/2);
    margin-top: 0px - (144/2);
    &:after {
      content: '';
      animation: emojishow infinite 1s linear;
      width: 144px;
      height: 144px;
      font-size: 999;
      font-size: 100px;
      margin: 0 auto;
      text-align: center;
      display: block;
    }
  }
}
@keyframes emojishow {
  from {
    content: '🌍';
  }
  33% {
    content: '🌎';
  }
  66% {
    content: '🌏';
  }
  to {
    content: '🌍';
  }
}
</style>

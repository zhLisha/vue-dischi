<template>
  <div class="loader flex">
    <span class="circle"></span>
    <span class="circle"></span>
    <span class="circle"></span>
  </div>
</template>

<script>

export default {
    name: 'LoadingPage'
}
</script>

<style lang="scss" scoped>
@import '@/style/common.scss';

.loader {
  height: calc(100vh - 60px);
  background-color: $mainColor;
  justify-content: center;
  align-items: center;

  .circle {
    display: inline-block;
    background-color: $secondColor;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    margin: 0 10px;
    transform:translate3d(0);
    animation: bounce 0.5s infinite alternate;
  }

  .circle:nth-child(2) {
    background-color: $smallTextColor;
    animation-delay: 0.2s;
  }

  .circle:nth-child(3) {
    background-color: $mainTextColor;
    animation-delay: 0.3s;
  }
}

@keyframes bounce {
  to {
    width: 40px;
    height: 40px;
    transform:translate3d(0, -30px, 0);
  }
}
</style>
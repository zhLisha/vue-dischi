<template>
  <div class="header">
    <div class="image-logo flex">
        <a href="#">
            <img src="@/assets/logo.png" alt="logo-brand">
        </a>
    </div>
  </div>
</template>

<script>
export default {
    name: 'HeaderSpotify'

}
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';

.header {
    height: 60px;
    background-color: $secondColor;

    .image-logo {
        padding: 10px 20px;

        img {
            width: 40px;
        }
    }
}
</style>
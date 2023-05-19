<script setup>
import { RouterView } from 'vue-router';
import Header from '@/components/Header.vue';

</script>

<template>
  <Header />
  <RouterView />
</template>

<style lang="less">
:root {
  --todoist-orange: #CB5647;
  --light-orange: #EABBB5;
  --main-gray: #808080;
}
@import '@/assets/main.less';
@media
(prefers-reduced-motion: no-preference) {
  html {
    scroll-behavior: smooth;
  }
}

</style>

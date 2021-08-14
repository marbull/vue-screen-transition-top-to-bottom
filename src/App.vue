<template>
  <ScreenTransitionUpToDown />
  <div id="container">
    <p>ここにコンテンツが入る</p>
  </div>
</template>

<script setup>
  import ScreenTransitionUpToDown from './components/ScreenTransitionUpToDown.vue';
</script>

<style scoped>
  /* 画面遷移の後現れるコンテンツ設定 */
  #container {
    opacity: 0;
  }

  /* bodyにappearクラスがついたら出現 */
  body.appear #container {
    animation-name: PageAnimeAppear;
    animation-duration: 1s;
    animation-delay: 0.8s;
    animation-fill-mode: forwards;
    opacity: 0;
  }

  @keyframes PageAnimeAppear {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }
</style>

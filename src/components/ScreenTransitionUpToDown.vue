<template>
  <div id="splash">
    <div id="splash-logo">ローディング</div>
  </div>
  <div class="splashbg"></div>
</template>

<script setup>
  import { onMounted } from '@vue/runtime-core';
  import $ from 'jquery';

  onMounted(() => {
    $(window).on('load', () => {
      // ロゴを１．２秒でフェードアウトする記述
      $('#splash-logo').delay(1200).fadeOut('slow');
      // ローディングエリア（splashエリア）を１．５秒でフェードアウトする記述
      $('#splash')
        .delay(1500)
        .fadeOut('slow', () => {
          $('body').addClass('appear');
        });
      $('.splashbg').on('animationend', () => {
        console.log('背景が伸びた後に動かしたいJSがある場合，ここに記載する');
      });
    });
  });
</script>

<style scoped>
  /* 共通CSS */
  #splash {
    position: fixed;
    width: 100%;
    height: 100%;
    background: #333;
    z-index: 9999999;
    text-align: center;
    color: #fff;
  }

  #splash-logo {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  /* 画面遷移アニメーション */
  .splashbg {
    display: none;
  }

  /* bodyにappearクラスがついたら出現 */
  body.appear .splashbg {
    display: block;
    content: '';
    position: fixed;
    z-index: 999;
    width: 100%;
    height: 100vh;
    top: 0;
    left: 0;
    transform: scaleY(0);
    /* 伸びる背景色の設定 */
    background: #333;
    animation-name: PageAnime;
    animation-duration: 1.2s;
    animation-timing-function: ease-in-out;
    animation-fill-mode: forwards;
  }

  @keyframes PageAnime {
    0% {
      transform-origin: top;
      transform: scaleY(0);
    }
    50% {
      transform-origin: top;
      transform: scaleY(1);
    }
    50.001% {
      transform-origin: bottom;
    }
    100% {
      transform-origin: bottom;
      transform: scaleY(0);
    }
  }
</style>

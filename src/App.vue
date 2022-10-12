<script setup>
import Editor from "./components/Editor.vue";
import IntroText from "./components/IntroText.vue";
</script>

<template>
  <nav class="navbar navbar-expand-md navbar-dark bg-dark mb-4" style="background-image: url(https://ipmdecisions.net/media/yzrdplvp/field-sunset.jpg?center=0.73495389107344177,0.5&mode=crop&width=2000&height=570&rnd=132192576870330000);">
  <div class="container" >
    <img src="./assets/icons/ipmdlogo.png" style="height: 30px; padding-right: 20px;"/>
    <a class="navbar-brand" href="#" style="margin-right: auto !important; margin-left: 0px !important;">DSS Metadata file editor</a>
    
  </div>
</nav>
<main class="container">
  <IntroText/>
  <Editor/>
</main>
</template>

<style>
@import './assets/base.css';

.bd-placeholder-img {
        font-size: 1.125rem;
        text-anchor: middle;
        -webkit-user-select: none;
        -moz-user-select: none;
        user-select: none;
      }

      @media (min-width: 768px) {
        .bd-placeholder-img-lg {
          font-size: 3.5rem;
        }
      }

      .b-example-divider {
        height: 3rem;
        background-color: rgba(0, 0, 0, .1);
        border: solid rgba(0, 0, 0, .15);
        border-width: 1px 0;
        box-shadow: inset 0 .5em 1.5em rgba(0, 0, 0, .1), inset 0 .125em .5em rgba(0, 0, 0, .15);
      }

      .b-example-vr {
        flex-shrink: 0;
        width: 1.5rem;
        height: 100vh;
      }

      .bi {
        vertical-align: -.125em;
        fill: currentColor;
      }

      .nav-scroller {
        position: relative;
        z-index: 2;
        height: 2.75rem;
        overflow-y: hidden;
      }

      .nav-scroller .nav {
        display: flex;
        flex-wrap: nowrap;
        padding-bottom: 1rem;
        margin-top: -1px;
        overflow-x: auto;
        text-align: center;
        white-space: nowrap;
        -webkit-overflow-scrolling: touch;
      }
</style>

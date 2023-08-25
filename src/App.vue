<template>
  <body class="asking-timer">
    <TheHeader />
    <TitleSetting />
        <Timer />
    <TheFooter />
  </body>
</template>

<script setup>
import TheHeader from './components/TheHeader.vue'
import Timer from './components/Timer.vue'
import TitleSetting from './components/TitleSetting.vue'
import TheFooter from './components/TheFooter.vue'

</script>

<style>
@import 'assets/css/destyle.css';
.asking-timer{
  font-family: 'Yu Mincho Light','YuMincho','Yu Mincho','游明朝体',sans-serif;
  text-align: center;
  line-height: 1.5;
}

.btn{
  color: #fff;
  background-color: #eb6100;
}
</style>
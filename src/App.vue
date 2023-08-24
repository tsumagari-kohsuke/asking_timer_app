<template>
  <body class="asking-timer">
    <TheHeader />
    <TitleSetting />
    <Timer />
    <TheFooter />
  </body>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import Timer from './components/Timer.vue'
import TitleSetting from './components/TitleSetting.vue'
import TheFooter from './components/TheFooter.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    Timer,
    TitleSetting,
    TheFooter
  }
}
</script>

<style>
@import 'assets/css/destyle.css';
.asking-timer{
  text-align: center;
  line-height: 1.5;
}
</style>
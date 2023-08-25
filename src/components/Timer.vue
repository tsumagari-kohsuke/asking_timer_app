<template>
  <div id="my_timer">
    <div class="my_timer">
      <span class="circle">
        <div class="my_time">
          {{ formatTime }}
        </div>
      </span>
      <br>
      <button class="btn" @click="start" v-if="!timerOn">Start</button>
      <button class="btn" @click="stop" v-if="timerOn">Stop</button>
      <button class="btn_left" @click="reset">Reset</button>
    </div>
  </div>
</template>

<script>
import {ref} from 'vue';

const initialMin = ref(15);
const initialSec = ref(0);
export default {
  name: 'my_timer',
  data() {
    return {
      min: initialMin.value,
      sec: initialSec.value,
      timerOn: false,
      timerObj: null,
      changeMode: false,
    }
  },
  methods: {
    count: function() {
      if (this.sec <= 0 && this.min >= 1) {
        this.min --;
        this.sec = 59;
      } else if(this.sec <= 0 && this.min <= 0) {
        this.complete();
      } else {
        this.sec --;
      }
    },
    reset: function(){
      this.min = initialMin.value;
      this.sec = initialSec.value;
      if (this.timerOn){
        this.stop();//強制的にタイマーストップ
      }
    },

    start: function() {
      let self = this;
      this.timerObj = setInterval(function() {self.count()}, 1000)
      this.timerOn = true; //timerがONであることを状態として保持
    },

    stop: function() {
      clearInterval(this.timerObj);
      this.timerOn = false; //timerがOFFであることを状態として保持
    },

    complete: function() {
      clearInterval(this.timerObj)
      alert('時間になりました。\n解決していなければ質問に行きましょう。')
    }
  },
  computed: {
    formatTime: function() {
      let timeStrings = [
        this.min.toString(),
        this.sec.toString()
      ].map(function(str) {
        if (str.length < 2) {
          return "0" + str
        } else {
          return str
        }
      })
      return timeStrings[0] + ":" + timeStrings[1]
    }
  }
}
</script>

<style scoped>
#my_timer {
  margin: 30px;
  display: flex;
  justify-content: center;
  line-height: 1;
}
.my_timer {
  font-size: 80px;
}
.btn {
  padding: 8px;
  border: 1px solid #0000;
  background-color: #03a9f4;
  border-radius: 6px;
  color: #fff;
  text-align: center;
  font-size: 14px;
  border-bottom: 5px solid #03a9f4;
  box-shadow: 0 3px 5px rgba(0, 0, 0, .3);
}
.btn_left{
  margin-left: 10px;
  padding: 8px;
  border: 1px solid #0000;
  background-color: #03a9f4;
  border-radius: 6px;
  color: #fff;
  text-align: center;
  font-size: 14px;
  border-bottom: 5px solid #03a9f4;
  box-shadow: 0 3px 5px rgba(0, 0, 0, .3);
}
.circle {
  display: inline-block;
  width: 300px;
  height: 300px;
  color: #fff;
  line-height: 100px;
  text-align: center;
  border-radius: 50%;
  border: solid 5px skyblue;
}
@import url("https://fonts.googleapis.com/css2?family=Stardos+Stencil:ital,wght@0,400&display=swap");
.my_time{
  margin-right: 10px;
  font-family: 'Stardos Stencil';
  font-style: italic;
  font-size: 85px;
  font-weight: 700;
  color: black;
  transform: translate(0, 100%);
}
</style>

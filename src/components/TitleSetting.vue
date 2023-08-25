<template>
  <div class="title_setting">
      <p><input type="text" class="title_input" v-model="taskTitle" v-if="!editmode" placeholder="疑問点を入力" /></p>
      <p class="task_title" v-if="editmode">【現在直面している問題点】</p>
      <p class="task_title" v-if="editmode">「{{taskTitle}}」</p>
      <p class="task_title" v-if="editmode">登録された時間 : {{currentTime}}</p>
      <button class="btn" @click="changeMode">
        {{ editmode ? '変更' : '登録' }}
      </button>
  </div>
</template>

<script setup>
import {ref} from 'vue';
const taskTitle = ref('');
const editmode = ref(false);
const currentTime = ref('');

const changeMode = () => {
  if (taskTitle.value !== ''){
    if(!editmode.value){
      const date  = new Date();
      let h = date.getHours();
      let m = date.getMinutes();
      let s = date.getSeconds();
      if(h < 10) h = "0" + h;
      if(m < 10) m = "0" + m;
      if(s < 10) s = "0" + s;
      currentTime.value = h + ":" + m + ":" + s;
    }
    editmode.value = !editmode.value;
  } else {
    alert("入力ボックスに課題を入力してから登録してください。");
  }
}

</script>

<style scoped>
.title_setting {
  margin: 30px;
}

.task_title {
  padding: 8px;
  font-size: 21px;
  text-align: center;
}

.title_input {
  width: 300px;
  padding: 8px;
  font-size: 20px;
  border: 1px solid #aaa;
  border-radius: 6px;
}

.btn {
  margin-top: 10px;
  padding: 8px;
  background-color: #333;
  border-radius: 6px;
  color: #fff;
  text-align: center;
  font-size: 14px;
  border-bottom: 5px solid #222;
  box-shadow: 0 3px 5px rgba(0, 0, 0, .3);
}
</style>
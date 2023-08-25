<template>
  <div class="title_setting">
      <div v-if="editmode" class="edit_area">
        <input type="text" class="title_input" v-model="taskTitle" placeholder="疑問点を入力" />

        <button class="btn" @click="register">登録</button>
      </div>
      
      <template v-if="!editmode">
        <p class="task_title">【現在直面している問題点】</p>
        <p class="task_title">「{{taskTitle}}」</p>
        <p class="task_title">登録された時間 : {{currentTime}}</p>

        <button class="btn" @click="enterEditMode">変更</button>
      </template>
  </div>
</template>

<script setup>
import {ref} from 'vue';
const taskTitle = ref('');
const editmode = ref(true);
const currentTime = ref('');

const register = () => {
  if (taskTitle.value !== ''){
    const date  = new Date();
    currentTime.value = formatDate(date.getHours(), date.getMinutes(), date.getSeconds());

    leaveEditMode();
  } else {
    alert("入力ボックスに課題を入力してから登録してください。");
  }
}

const enterEditMode = () => {
  editmode.value = true;
}

const leaveEditMode = () => {
  editmode.value = false;
}

const formatDate = (h, m, s) => {
  if(h < 10) h = "0" + h;
  if(m < 10) m = "0" + m;
  if(s < 10) s = "0" + s;
  return h + ":" + m + ":" + s;
}

</script>

<style scoped>
.title_setting {
  margin: 30px;
}

.edit_area {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
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
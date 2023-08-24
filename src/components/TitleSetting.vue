<template>
  <div class="title_setting">
      <p><input type="text" class="title_input" v-model="taskTitle" v-if="!editmode" placeholder="課題を入力" /></p>
      <p type="text" class="task_title" v-if="editmode">{{taskTitle}}</p>
      <button class="btn" @click="changeMode">
        {{ editmode ? '変更' : '登録' }}
      </button>
  </div>
</template>

<script setup>
import {ref} from 'vue';
const taskTitle = ref('');
const editmode = ref(false);

const changeMode = () => {
  if (taskTitle.value !== ''){
    editmode.value = !editmode.value 
  } else {
    alert("課題を登録してください。")
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
  padding: 8px;
  background-color: #03a9f4;
  border-radius: 6px;
  color: #fff;
  text-align: center;
  font-size: 14px;
}
</style>
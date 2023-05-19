<script setup>
import { reactive } from 'vue'
const props = defineProps({
  toggleTodosCreateForm: {
    type: Function,
    required: true
  }
});
const emit = defineEmits(['create-todo']);

const todoState = reactive({
  todo: "",
  invalid: null,
  errMsg: ""
})

function toggleForm() {
  props.toggleTodosCreateForm();
}

const createTodo = () => { 
  todoState.invalid = null;
  if (todoState.todo !== "") {
    emit('create-todo', todoState.todo);
    todoState.todo = "";
    return;
  }
  todoState.invalid = true;
  todoState.errMsg = "Cannot leave field empty"
}
</script>

<template>
  <div>
    <div class="input-wrap" >
      <input type="text" :class="{ 'input-err': todoState.invalid }" v-model="todoState.todo" placeholder="예. 매일 독서 p3 @목표#공부" />
      <div class="button-group">
        <button id='btn-create' class="btn-orange" @click="createTodo()">작업 추가</button>
        <button class="btn-white" @click="toggleForm()">취소</button>
      </div>
    </div>
    <p v-show="todoState.invalid" class="error-msg">{{ todoState.errMsg }}</p>
    
  </div>
</template>


<style lang='less' scoped>
input:focus ~ div #btn-create {
  background: var(--todoist-orange);
  cursor: pointer;
}
.input-wrap input {
  width: 100%;
  border-radius: 7px;
  
  margin-bottom: 10px;
  padding: 8px;
  font-size: 10pt;
}
.input-err {
  border: 1px solid red;
}
.error-msg {
  margin-top: 6px;
  font-size: 12px;
  color: red;
}
button {
  margin-right: 11px;
  border-radius: 5px;
  padding: 2px 7px;
  font-size: 10pt;
}
.btn-orange {
  background-color: var(--light-orange);
  color: white;
  border: 1px solid var(--todoist-orange);
}
.btn-white {
  background-color: white;
  border: 1px solid var(--main-gray);
  cursor: pointer;
}

</style>
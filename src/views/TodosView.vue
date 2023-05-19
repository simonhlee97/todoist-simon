<script setup>
import { ref } from 'vue'
import { uid } from 'uid'
import TodosCreateForm from '@/components/TodosCreate.vue';
import TodoItem from '../components/TodoItem.vue';
const todoList = ref([])
const showTodosCreateForm = ref(false);

function toggleTodosCreateForm() {
  showTodosCreateForm.value = !showTodosCreateForm.value;
}

const createTodo = (todo) => { 
  todoList.value.push({
    id: uid(),
    todo: todo,
    isCompleted: null,
    isEditing: null,
  })
}

const toggleTodoComplete = (todoIndex) => { 
  todoList.value[todoIndex].isCompleted =! todoList.value[todoIndex].isCompleted
}

const deleteTodo = (todoId) => { 
  todoList.value = todoList.value.filter((todo) => todo.id !==todoId)
}

// defineEmits(["show-todo-form"]);
</script>

<template>
  <main>
    <h3><span class="today">오늘</span> <span class="date">목 4월 21일</span></h3>
    <ul class="todo-list" v-if="todoList.length > 0">
      <TodoItem v-for="(todo, index) in todoList" :todo="todo" :index="index" 
        @toggle-complete="toggleTodoComplete" 
        @delete-todo="deleteTodo"
      />
    </ul>
    <div class="empty-list" v-else>
      <p class="empty-text">할 일이 없습니다</p>
      <p class="empty-subtext">남은 하루도 즐겁게 보내세요.</p>
    </div>
    
    <div v-if="!showTodosCreateForm" class="add-todo-control" @click="toggleTodosCreateForm">
      <i class="plus-icon fa-solid fa-plus"></i> <span class="add-icon-label">작업 추가</span>
    </div>

    <TodosCreateForm v-show="showTodosCreateForm" @create-todo="createTodo" :toggleTodosCreateForm="toggleTodosCreateForm" />
  </main>
</template>

<style>
main {
  padding: 34px 10px 0px 10px;
  max-width: 800px;
  margin: 0 auto;
}
h3 {
  margin-bottom: 0.8em;
}
.empty-list {
  width: 400px;
  height: 50px;
  margin: auto;
  position: absolute;
  top: 0; left: 0; bottom: 0; right: 0;
}
.empty-text {
  font-size: 16px;
  line-height: 21px;
  text-align: center;
  margin-bottom: 15px;
}
.empty-subtext {
  line-height: 18px;
  font-style: normal;
  font-weight: 400;
  font-size: 13px;
  color: #777777;
  text-align: center;
}
.todo-form {
  display: none;
}
.add-todo-control {
  padding: 12px 0px;
  cursor: pointer;
}
h3 {
  display: flex;
  align-items: center;
}
.todo-list {
  list-style-type: none;
  margin: 8px 0;
  padding: 8px 0;
}
.plus-icon {
  color: var(--todoist-orange);
}
.add-icon-label {
  color: #afa8a8;
  font-size: 10pt;
  font-weight: 300;
}
.date {
  color: #afa8a8;
  font-size: 9.5pt;
  font-weight: 300;
}
.today {
  margin-right: 6px;
}
</style>

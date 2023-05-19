<script setup>
const props = defineProps({
  todo: {
    type: Object,
    required: true
  },
  index: {
    type: Number,
    required: true
  }
});
defineEmits(["toggle-complete", "delete-todo"]);
</script>

<template>
  <li>
  <div class="todo">
    <span class="checkbox"><input type="checkbox" :checked="todo.isCompleted" @input="$emit('toggle-complete', index)" /></span>
    <span v-if="todo.isEditing"><input  type="text" :value="todo.todo" /></span>
    <span v-else :class="{'completed-todo' : todo.isCompleted}" class="todo-text">{{ todo.todo }}</span>
    <span class="delete-btn"><i class="fa-solid fa-trash-can" @click="$emit('delete-todo', todo.id)"></i></span>
  </div>
  </li>

  <!-- <div class="todo-actions">
    <i v-if="todo.isEditing" class="fa-regular fa-square-check"></i>
    <i v-else class="fa-solid fa-pencil"></i>
  </div> -->
</template>


<style lang='less' scoped>

.todo {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  padding: 11px 0;
  height: 40px;
  border-bottom: 1px solid #d3cfcf6e;
  margin-bottom: 3px;
  &:hover {
    .delete-btn {
      opacity: 1;
      cursor: pointer;
    }

  }
}
.completed-todo {
  text-decoration: line-through;
}

// TEST TEST TEST TEST TEST TEST
.form-control {
  display: grid;
  grid-template-columns: 1em auto;
  gap: 0.5em;
}

.form-control--disabled {
  color: var(--form-control-disabled);
  cursor: not-allowed;
}

input[type=checkbox] {
  /* Add if not using autoprefixer */
  -webkit-appearance: none;
  /* Remove most all native input styles */
  -moz-appearance: none;
       appearance: none;
  margin: 0;
  color: var(--main-gray);
  width: 1em;
  height: 1em;
  border: 0.04em solid var(--main-gray);
  border-radius: 50%;
  transform: translateY(-0.065em);
  display: grid;
  place-content: center;
}

input[type=checkbox]::before {
  content: "";
  width: 0.5em;
  height: 0.5em;
  -webkit-clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
          clip-path: polygon(14% 44%, 0 65%, 50% 100%, 100% 16%, 80% 0%, 43% 62%);
  transform: scale(0);
  transform-origin: bottom left;
  transition: 120ms transform ease-in-out;
  box-shadow: inset 1em 1em var(--form-control-color);
  /* Windows High Contrast Mode */
  background-color: CanvasText;
}

input[type=checkbox]:checked::before {
  transform: scale(1);
}

input[type=checkbox]:disabled {
  --form-control-color: var(--form-control-disabled);
  color: var(--form-control-disabled);
  cursor: not-allowed;
}

.todo span:nth-child(2) {
  margin-left: 10px;
  width: 100%;
}
.todo span:nth-child(3) {
  padding: 0 6px;
}
.fa-trash-can {
  color: var(--todoist-orange);
}
.todo-text {
  font-family: 'Apple SD Gothic Neo', Arial, Helvetica, sans-serif;
  font-weight: 400;
  font-size: 14px;
  letter-spacing: 0.3px;
  color: #202020;
}

.delete-btn {
  opacity: 0;
  transition: 150ms ease-in-out;
}
</style>
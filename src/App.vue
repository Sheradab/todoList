<template class="template">
  <div class="todo_wrapper">
    <div class="title has-text-centered">Мой Todo лист!</div>
    <form @submit.prevent="addTodo">
      <div class="field is-grouped mb-10">
        <p class="control is-expanded ">
          <input v-model="newTodoContent" class="input" type="text" placeholder="Опубликовать">
        </p>
        <p class="control">
          <button :disabled="!newTodoContent" class="button is-info ">
            Добавить
          </button>
        </p>
      </div>
    </form>

    <div v-for="todo in todos" :key="todo.id" class="card mt-5">
      <div class="card-content">
        <div class="content">
          {{todo.content}}
        </div>
        <div>
          <div class="button mr-1 is-success">✔</div>
          <div class="button is-danger">⛌</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

//import
import {ref} from "vue";
import { v4 as uuidv4 } from 'uuid';

//todos
const todos = ref ([

]);

//add Todo
const newTodoContent = ref("");

const addTodo = () =>{
  const newTodo = {
    id: uuidv4(),
    content: newTodoContent.value,
    done: false
  }
  todos.value.unshift(newTodo);
}

</script>

<style>
@import "C:\Users\RUDAKi\app2\node_modules\bulma\css\bulma.min.css";

.todo_wrapper {
  max-width: 400px;
  padding: 20px;
  margin: 0 auto;
}

.card-content {
  display: flex;
  justify-content:space-around;
  flex-wrap: wrap;
}

</style>
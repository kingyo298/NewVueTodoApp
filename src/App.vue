<template>
  <div id="app">
    <div class='container mt-5' id="container">
      <div class="input-group mb-3 w-50">
          <input type="text" class="form-control" placeholder="write a task" aria-label="Recipient's username" aria-describedby="button-addon" v-model="text">
          <button class="btn btn-outline-secondary" type="button" id="button-addon" @click="addTodoItem" :disabled="text === ''">Create</button>
      </div>
      <div v-if="todos.length > 0" id="cards">
        <div class="card w-50 my-1" v-for="(todo,index) in todos" :key="index">
          <div class="card-body">
            <h5 class="card-title">TODO {{index}} : {{todo}}</h5>
            <button class="btn btn-primary mt-2" @click="deleteTodoItem(index)">Delete</button>
          </div>
        </div>
      </div>
      <p v-else>まだTODOリストがありません。</p>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
  const todos = ref<string[]>([])
  const text = ref<string>("")
  const isDisabled = ref<boolean>(true)

  const addTodoItem = () => {
    todos.value.push(text.value);
    text.value = "";
  }
  const deleteTodoItem = (index: number) => {
    todos.value.splice(index,1);
  }
</script>

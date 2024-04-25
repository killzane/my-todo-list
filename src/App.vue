<script setup>
import { ref } from 'vue'
const newTask = ref('')
const todoList = ref([
  { id: 'a0', taskName: 'Cras justo odio', completed: false },
  { id: 'a1', taskName: 'Cras justo odio', completed: true }
])

const addToList = function (taskName) {
  alert(taskName)
}
</script>

<template>
  <div id="app" class="container my-3">
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <span class="input-group-text" id="basic-addon1">待辦事項</span>
      </div>
      <input type="text" class="form-control" placeholder="準備要做的任務" v-model="newTask" />
      <div class="input-group-append">
        <button class="btn btn-primary" type="button" @click="addToList(newTask)">新增</button>
      </div>
    </div>
    <div class="card text-center">
      <div class="card-header">
        <ul class="nav nav-tabs card-header-tabs">
          <li class="nav-item">
            <a class="nav-link active" href="#">全部</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">進行中</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">已完成</a>
          </li>
        </ul>
      </div>
      <ul class="list-group list-group-flush text-left">
        <li class="list-group-item" v-for="item in todoList">
          <div class="d-flex">
            <div class="form-check">
              <input type="checkbox" class="form-check-input" :id="item.id" />
              <label
                class="form-check-label"
                :class="{ completed: item.completed }"
                :for="item.id"
                >{{ item.taskName }}</label
              >
            </div>
            <button type="button" class="close ml-auto" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
        </li>
        <li class="list-group-item">
          <input type="text" class="form-control" />
        </li>
      </ul>
      <div class="card-footer d-flex justify-content-between">
        <span>還有 3 筆任務未完成</span>
        <a href="#">清除所有任務</a>
      </div>
    </div>
  </div>
</template>

<style lang="css" src="@/assets/bootstrap.css"></style>
<style scoped>
.completed {
  text-decoration: line-through;
}
</style>

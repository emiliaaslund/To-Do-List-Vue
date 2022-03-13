<script setup>
import ToDoList from "./components/ToDoList.vue";
</script>

<template>
  <div id="app"></div>
  <h1 class="app-title">MY TO-DO LIST</h1>
  <ToDoList />
</template>

<style>
* {
  font-family: "Lato", sans-serif;
  font-weight: 500;
  list-style-type: none;
}

body {
  background: #e8ebf3;
  height: 100vh;
  display: flex;
  justify-content: center;
}
.app-title {
  font-family: "Playfair Display", serif;
  text-align: center;
  color: #818ea8;
  font-size: 70px;
  text-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
}
</style>

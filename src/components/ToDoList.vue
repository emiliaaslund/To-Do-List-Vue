<script>
import { ref } from "vue";

export default {
  name: "TodoList",
  data() {
    return {
      newToDo: ref(""),
      todo: ref([]),
      checked: "false",
    };
  },
  methods: {
    add() {
      this.todo.push({
        text: this.newToDo,
        id: new Date().valueOf(),
        checked: false,
      }),
        (this.newToDo = "");
    },
    removeToDo(i) {
      this.todo.splice(i, 1);
    },
  },
};
</script>

<template>
  <!-- input field -->
  <div className="container">
    <input
      className="input"
      type="text"
      placeholder="Enter item.."
      v-model="newToDo"
      @keyup.enter="add()"
    />
    <button class="add-btn" @click="add()">ADD</button>
  </div>

  <!-- todolist -->
  <ul>
    <li class="container" v-for="(todo, i) in todo" :key="todo.id">
      <input class="checkbox" type="checkbox" v-model="todo.checked" />
      <span :class="{ completed: todo.checked }">
        <span class="todoText">{{ i + 1 }}:{{ todo.text }}</span>
      </span>
      <button class="remove-btn" @click="removeToDo(i)">X</button>
    </li>
  </ul>
</template>

<style scoped>
.add-btn {
  background: #aeb8ce;
  width: 80px;
  margin: 10px;
  font-size: 18px;
  height: 35px;
  color: rgb(0, 0, 0);
  border: none;
  border-radius: 14px;
  box-shadow: rgba(0, 0, 0, 0.05) 0px 0px 0px 1px;
}

.remove-btn {
  font-size: 17px;
  background: #aeb8ce;
  border: none;
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.05) 0px 0px 0px 1px;
}

.remove-btn:hover,
.add-btn:hover {
  cursor: pointer;
}

.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 25px;
  background: rgb(255, 255, 255);
  box-shadow: rgba(100, 100, 111, 0.2) 0px 7px 29px 0px;
  padding: 30px;
  text-align: center;
  max-width: 500px;
  margin: 10px;
}

ul {
  padding: 0;
}

.input {
  font-size: 20px;
  width: 350px;
  height: auto;
  padding: 12px 20px;
  margin: 10px;
  border: none;
  box-shadow: rgba(0, 0, 0, 0.05) 0px 0px 0px 1px;
  border-radius: 12px;
  outline: none;
  resize: none;
}

.completed {
  text-decoration: line-through;
  color: #618d5fce;
  font-size: 20px;
}

.todoText {
  font-size: 20px;
  text-align: center;
}

input[type="checkbox"] {
  width: 20px;
  height: 20px;
  cursor: pointer;
}
</style>

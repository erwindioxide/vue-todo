<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add To-do..." />
      <input type="submit" value="Add" class="btn" />
    </form>
  </div>
</template>

<script>
// import { v4 as uuid } from "uuid";
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const newTodo = {
        // id: uuid,
        title: this.title,
        completed: false
      };
      // Send up to parent
      this.$emit("add-todo", newTodo);
      //clears the input onsubmit
      this.title = "";
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
input [type="text"] {
  flex: 10;
  padding: 5px;
}

input[type="submit"] {
  flex: 2;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 2px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
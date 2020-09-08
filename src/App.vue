<template>
  <div class="container mt-5">
    <nav aria-label="breadcrumb">
      <ol class="breadcrumb">
        <li class="breadcrumb-item active" aria-current="page">Todo List App</li>
      </ol>
    </nav>
    <div class="container card mt-3 align-items-center">
      <Todo></Todo>
      <!-- <Ui></Ui> -->
    </div>
  </div>
</template>

<script>
import Todo from "./todos/Todo";
export default {
  data() {
    return {
      name: "hello world"
    };
  },
  components: {
    Todo
  }
};
</script>

<style>
.header {
  height: 50px;
  background: cornflowerblue;
}
</style>
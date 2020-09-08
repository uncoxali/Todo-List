<template>
  <div class="col-sm-12">
    <div class="d-flex p-3">
      <div class="col-sm-6">
        <input type="text" class="form-control" placeholder="Add Todo..." v-model="user.todos" />
      </div>
      <div class="col-sm-6">
        <button class="btn btn-success btn-block" @click="addTodos">Add Todos</button>
      </div>
    </div>
    <div class="clearfix"></div>
    <hr />

    <ul class="d-block">
      <span class="d-flex justify-content-center">
        <b-col md="6" class="mb-3" v-if="load">
          <b-icon icon="three-dots" animation="cylon" font-scale="4"></b-icon>
        </b-col>
      </span>
      <li
        class="list-group-item list-group-item-action"
        v-for="(item,index) in user.todolist"
        :key="item"
      >
        <p>
          {{item}}
          <a class="float-right remove" @click="remove(index)">
            <b-icon icon="trash-fill" class="mr-3"></b-icon>
          </a>
          <a class="float-right edit">
            <b-icon icon="pencil-square" class="mr-3"></b-icon>
          </a>
          <a class="float-right pin" @click="hideTodo(index)">
            <b-icon icon="paperclip" class="mr-3"></b-icon>
          </a>
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
// import Ui from "./todos/Ui";

export default {
  data() {
    return {
      user: {
        todolist: [],
        todos: ""
      },
      load: false,
      hide: ""
    };
  },
  methods: {
    addTodos() {
      if (this.user.todos != "") {
        this.load = true;
        setTimeout(() => {
          this.load = false;
          this.user.todolist.unshift(this.user.todos);
          this.user.todos = "";
        }, 500);
      }
    },
    hideTodo(id) {
      this.hide;
      console.log(id);
    },

    remove(id) {
      this.load = true;
      if (this.user.todolist != "") {
        setTimeout(() => {
          this.load = false;
          this.$delete(this.user.todolist, id);
        }, 300);
      }
    }
  }
};
</script>

<style scoped>
.remove {
  cursor: pointer;
  color: cornflowerblue;
  font-size: 25px;
}
.remove:hover {
  color: red;
}
.edit {
  cursor: pointer;
  color: cornflowerblue;
  font-size: 25px;
}
.edit:hover {
  color: dodgerblue;
}
.pin {
  cursor: pointer;
  color: cornflowerblue;
  font-size: 25px;
}
.pin:hover {
  color: hotpink;
}
</style>
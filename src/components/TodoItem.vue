<template>
  <body>
  <div class="container">
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
      <p>
        <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed" />
        {{todo.title}}
        <button class="btn btn-dark" @click="updateTodo">Update</button>
        <button class="btn btn-light" @click="$emit('del-todo', todo.id)" >Remove</button>
      </p>
    </div>
    <div v-if="this.flag">
      <form @submit="updateTodoMethod">
        <div class="form-group">
          <input
            class="form-control"
            v-model="updateTitle"
            type="text"
            :placeholder="title"
            name
            id
          />
        </div>
        <div class="form-group">
<!--          <button class="btn btn-danger">Updatee</button>-->
<!--          <button class="btn button-try" role="button">Updateee</button>-->

        </div>
      </form>
    </div>
  </div>
  </body>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo", "todos", "title", "id"],
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
    updateTodo() {
      this.flag = !this.flag;
    },
    updateTodoMethod(e) {
      e.preventDefault();
      console.log(this.title);
      console.log(this.id);
      this.todos.filter((todo) => {
        if (todo.id == this.id) {
          todo.title = this.updateTitle;
        }
      });
      this.flag = false
    },
  },
  data() {
    return {
      flag: false,
      updateTitle: "",
    };
  },
};
</script>

<style scoped>
.todo-item {
  background: rgb(149, 173, 190);
  padding: 10px;
  margin: 20px;
  font-family: pigment demo font;

  border-bottom: 1px #ccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.
/*new try*/
body{
  margin: 10;
  padding: 10;
  background: #ffffff;
}
.middle{
  position: absolute;
  top: 10%;
  left: 20%;
  transform: translate(-50%,-50%);
}
.btn{
  position: relative;
  /*display: block;*/
  /*color: #000000;*/
  font-size: 12px;
  font-family: "bodoni";
  float: right;
  /*text-decoration: none;*/
  /*border-radius: 10%;*/
  /*margin: 30px 0;*/
  /*background: rgba(48, 243, 35, 0.5);*/
  /*border: 2px solid rgba(29, 146, 226, 0.5);*/
  padding: 5px 15px;
  margin-right: 6px;
  /*text-transform: uppercase;*/
  /*overflow: visible;*/
  /*transition: 1s all ease;*/
  /*top: 40%;*/
  /*left: 80%;*/

}
.btn::before{
  background: rgba(15, 21, 42, 0.5);
  /*content: "";*/
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  z-index: 1;
  transition: all 0.6s ease;
}



.btn2{
  position: relative;
  /*display: block;*/
  color: whitesmoke;
  font-size: 12px;
  font-family: "bodoni";
  float: right;

}
.btn2::before{
  background: rgba(15, 21, 42, 0.5);
  /*content: "";*/
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  z-index: 1;
  transition: all 0.6s ease;
}


</style>


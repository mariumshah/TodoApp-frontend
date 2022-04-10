<template>
  <body style="background-color:#364F6B">
    <div class="container" style="background-color:#364F6B">
        <br>
        <h1 class="text-center" style="color:white">To-do App</h1>
        <br><br>
        <form @submit="addTodo">
        <div class="form-group">
            <input required type="text" v-model="title" placeholder="Enter task here" name="title" id="" class="form-control">
        </div>
        <div class="form-group">
            <button class="btn btn-block btn-success">
                Add Task
            </button>
        </div>
        </form>
    </div>
  </body>
</template>
<script>

export default {
  name: "AddTodo",
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
        e.preventDefault()
      const newTodo = {
        id:Date.now(),
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);

      this.title = '';
    }
  }
}
</script>

<style scoped>

</style>
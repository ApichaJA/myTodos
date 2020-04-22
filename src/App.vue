<template>
  <div id="app">
    <div class="container">
      <div class="row">
        <div class="col-12 py-5">
          <h1>My to-dos</h1>
        </div>
      </div>
      <div class="row mb-3">
        <div class="col-12 col-sm-10 col-md-8 cl-lg-6">
      <input
        class="form-control"
        v-on:keyup.enter="submit"
        v-model="eventInput"
        placeholder="Create a new to-do..."
      />
        </div>
      </div>
      <div class="row">
        <div class="col-12 col-sm-10 col-lg-6">
          <ul class="list-group">
            <li
              class="d-flex align-items-center list-group-item"
              v-for="Mytodos in eventTodos"
              :key="Mytodos.id"
            >
              <button :style="Mytodos.completed ? { 'text-decoration': 'line-through' } : null" @click="Mytodos.completed = !Mytodos.completed" v-show="onEdit != Mytodos" class="btn border-0 flex-grow-1 text-left shadow-none">
                <span>{{Mytodos.messageTodos}}</span>
              </button>
              <input class="form-control"
                v-show="onEdit == Mytodos"
                v-on:keyup.enter="submitEdit"
                v-model="Mytodos.messageTodos"
              />
              <button
                class="btn btn-outline-primary border-0 ml-2 edit"
                @click="editTodos(Mytodos)"
              >
                <span class="fa fa-edit"></span>
              </button>
              <button class="btn btn-outline-danger border-0 delete" @click="deleteTodos(Mytodos)">
                <span class="fa fa-trash"></span>
              </button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      isClicked: false,
      onEdit: false,
      eventInput: "",
      eventTodos: [
        { id: 0, messageTodos: "Do the dishes", completed: false },
        { id: 1, messageTodos: "Take out the trash", completed: false },
        { id: 2, messageTodos: "Finish doing laundry", completed: false }
      ]
    };
  },
  methods: {
    submit() {
      this.eventTodos.push({
        messageTodos: this.eventInput,
        id: this.eventTodos.length,
        completed: false
      });
      this.eventInput = "";
    },
    submitEdit() {
      this.eventTodos.messageTodos = this.Mytodos;
      this.onEdit = false;
    },
    deleteTodos(Mytodos) {
      this.eventTodos.splice(this.eventTodos.indexOf(Mytodos), 1);
    },
    editTodos(Mytodos) {
      this.onEdit = Mytodos;
    },
  }
};
</script>

<style>
@import "assets/styles/main.css";
</style>
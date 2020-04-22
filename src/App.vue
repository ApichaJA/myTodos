<template>
  <div id="app">
    <link rel=stylesheet href=https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.4.1/css/bootstrap.min.css>
    <link
      rel="stylesheet"
      href="https://use.fontawesome.com/releases/v5.2.0/css/all.css"
      integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ"
      crossorigin="anonymous"
    />
    <div class="container">
      <h1>My to-dos</h1>
      <input
        class="col-12 col-sm-10 col-md-8 cl-lg-6"
        v-on:keyup.enter="submit"
        v-model="eventInput"
        placeholder="Create a new to-do..."
      />
      <div class="row">
        <div class="col-12 col-sm-10 col-lg-6">
          <ul class="list-group">
            <li class="d-flex align-items-center list-group-item" v-for="Mytodos in eventTodos" :key="Mytodos.id">
              <button data-v-216cc175="" class="btn border-0 flex-grow-1 text-left shadow-none">
                <span v-show="onEdit != Mytodos">{{Mytodos.messageTodos}}</span>
                </button>
                <input
                  class="flex-grow-1"
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
                <button
                  class="btn btn-outline-danger border-0 delete"
                  @click="deleteTodos(Mytodos)"
                >
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
      onEdit: false,
      eventInput: "",
      eventTodos: [
        { id: 0, messageTodos: "Do the dished" },
        { id: 1, messageTodos: "Take out the trash" },
        { id: 2, messageTodos: "Finish doing laundry" }
      ]
    };
  },
  methods: {
    submit() {
      this.eventTodos.push({
        messageTodos: this.eventInput,
        id: this.eventTodos.length
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
    }
  }
};
</script>

<style>
@import "assets/styles/main.css";
</style>
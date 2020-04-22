<template>
  <div id="app">
    <h1>My to-dos</h1>
    <input v-on:keyup.enter="submit" v-model="eventInput" placeholder="Create a new to-do...">
    <ul class="row">
      <li v-bind:class="{ active: active }" v-for="Mytodos in eventTodos" :key="Mytodos">
        <div class="myTodos">
          <label v-if="onEdit">{{Mytodos.title}}</label>
          <input v-if="showEdit" v-on:keyup.enter="submitEdit" v-model="Mytodos.title">
          <button class="edit" @click="editTodos(Mytodos)">edit</button>
          <button class="delete" @click="deleteTodos(Mytodos)">delete</button>
        </div>
      </li>
    </ul>
    <MyTodos/>
  </div>
</template>

<script>

export default {
  name: 'app',
  data(){
    return{
      onEdit: true,
      showEdit:false,
      eventInput:"",
      eventTodos:[
        {id: 0, title: 'Do the dished'},
        {id: 0, title: 'Take out the trash'},
        {id: 0, title: 'Finish doing laundry'},
      ]
    }
  },
  methods: {
    submit(){
      this.eventTodos.push({
        title: this.eventInput,
        id: 1
      })
    this.eventInput = ""
    },
    submitEdit(){
      this.eventTodos.title = this.Mytodos
      this.onEdit = true,
      this.showEdit = false
    },
    deleteTodos(Mytodos){
      this.eventTodos.splice(this.eventTodos.indexOf(Mytodos), 1);
    },
    editTodos(){
      this.onEdit = false,
      this.showEdit = true
    }
  },
}
</script>

<style>
body {
  margin: 0;
  box-sizing: border-box;
}
.myTodos{
  display: flex!important;
  padding: .75rem 1.25rem;
}
.Done{
  text-decoration: line-through;
}
#app {
  font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",
  Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif,
  "Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol","Noto Color Emoji";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

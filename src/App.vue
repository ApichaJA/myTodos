<template>
  <div id="app">
    <h1>My to-dos</h1>
    <input v-on:keyup.enter="submit" v-model="eventInput" placeholder="Create a new to-do...">
    <ul class="row">
      <li v-for="Mytodos in eventTodos" :key="Mytodos">
        <div class="myTodos">
          <label>{{Mytodos.title}}</label>
          <button class="edit">edit</button>
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
    deleteTodos(Mytodos){
      this.eventTodos.splice(this.eventTodos.indexOf(Mytodos), 1);
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
